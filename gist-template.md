# Regex for matching and patterns
 Regex or regular expression, is a string of text that helps search for, validate, find, or format text input by searching within the text for matching criteria. These are often used within multiple programming languages and can be used within search engines.

## Summary
To simplfy the above expression, this Regex is seaching for a character group of any number of characters, followed by the '@' symbol, then another character group set, followed by a ".", then finally ending with a third character group between 2 and 6 characters total. The following guide has been created to help budding developers understand each section of code, what it does, and how it is implemented.

Patterns used to match character combinations in strings are called regular expressions. Regular expressions are also objects in JavaScript.

These patterns are used with the exec() and test() methods of RegExp, and with the match(), matchAll(), replace(), replaceAll(), search(), and split() methods of String."

A regular expression's purpose is to make it easier for users to sort and locate important sets of strings that they might need for some reason.They might be sorting web URLs or collecting telephone numbers for a database.Regex is a common name for regular expressions.

This regex /^(https?://)?([\da-z.-]+).([a-z.]{2,6})([/\w .-])/?$/ matches a URL.

The URL matching regex /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/  is used.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Author](#author)

## Regex Components
Multiple parts of regular expressions can shape any search pattern you're working on.

The most typical components include:Anchors, quantifiers, character classes, bracket expressions, and other similar terms can become quite complicated when used in conjunction with regular expressions.Using particular components, you can basically find any string combination.Let's take a look, starting with the anchors, to get more information.

### Anchors
When using regex (regular expression), anchors are typically used to match a position in the string rather than a single character or set of characters.This means that you can match any character's position before, after, or between them. The caret ^ matches the position before the first character in a string, while the $ matches right after the last character in the string.

In our email regex example, we can see these as the ^ and $ characters: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Extracting them out looks like: /^$/

(Remember the / are to denote the start and end of the regular expression itself. )

After the first / we can see the ^ which translates into "start searching from the start of the string"

Before the final / we can see the $ which translates into "... and stop searching at the end of the string"

When used together, these two effectively inform the expression as a whole that we must evaluate the entire string rather than merely matching specific portions.If we were to evaluate a string like this, let's say we did not have it in our email illustration:

.....@gmail.com test ahhhh

.....@gmail.com test ahhh

The email part of the string would be returned as a match, but the rest of the string would not.We don't want this to happen; if the string we get isn't just an email, we don't want it to pass at all. However, including the anchors once more:

.....@gmail.com test ahhh no longer has any matches, while:

.....@gmail.com is now a perfect match!

They are used to instruct the expression to search/query only a very narrow range of characters.
### Quantifiers

Quantifiers are used to match the number of instances a character or group in a string of text.
* is used to match 0 or more times within the string
+ is used to match 1 or more times within the string
? is used to match only 0 or 1 time within the string
{} are used to match within a set limit
Placing a number alone within {} will match exactly that number of times within the string
A number followed by a comma within {} will match AT LEAST that number of times within the string
Two numbers separated by a comma within {} will match AT LEAST the first number of times and AT MOST the second number

As you can see in the Regex there are two quantifiers: + and {2,6}
The + will match will match an email with 1 or more of the characters or sequence listed immediately before it
{2,6} will match an email that has a minimum of 2 but no more than 6 of the previous listed characters or sequence at the end of the address

### Character Classes
Character classes are used to match any character or symbol from a certain set of characters
\d is used to match any digits between 0-9 \s is used to match a space or tab
\w is used to match a word including lowercase and capital letters, numbers, and underscores

Within the matching an email Regex, we can see \d being used after the @ symbol to signify any digit found here would match

Grouping and Capturing
Grouping is done using () to group certain parts of the string together for independent matching
In the email Regex there are 3 groups:
([a-z0-9_\.-]+)
([\da-z\.-]+)
([a-z\.]{2,6})
Each group has their own quantifiers, bracket expressions, and character classes to match within the email string as a whole
### Grouping and Capturing

Treating multiple characters as a single unit can be accomplished by grouping them together, or "capturing" groups.By using parentheses around the characters you want to group together, you can make them.You can use quantifiers on any member of the group and check the entire group for a match thanks to this.In our example email:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We have three groups

([a-z0-9_\.-]+) ([\da-z\.-]+) ([a-z\.]{2,6})

We have a character set with a quantifier for each group.The first two sets look for at least one match, while the final set in the last group looks for characters that match between 2 and 6.

The three sections of an email, with the exception of the @ and, are represented by these three groups.for the site itself)

.....@gmail.com

Because we are verifying that there is the appropriate quantity of data as well as valid data all over the place, grouping is particularly useful in this situation.Similar to grouping in mathematics, everything within a parenthesis will be evaluated on its own before being tested in the expression as a whole.

### Bracket Expressions
Brackets are used to indicate a strict set of characters to match. Typically these will be done using a range of digits [0-9], letters [a-z], or both [a-z0-9] They may also include special characters [a-z0-9_\.-]. This will match any letters, numbers, underscore, period, or hyphen.

### Greedy and Lazy Match

The default quantifiers try to match as many instances of a particular pattern as possible because they are greedy.However, they may also be lazi, matching as few instances of a particular pattern as they can.? is a quantifier on its own, but if it is added after another quantifier (or even itself), the matching mode changes from greedy to lazy.

For example, if I have the follow regex:

/a+/

And the following string:

aaaaaaa

It will match the whole string as its in greedy mode; its gonna try to match as MANY occurrences of the 'a' as possible.

aaaaaaa

However if I add a ? to the end of the regex expression:

/a+?/

It will only match the first instance of 'a':

aaaaaaa

As its now in lazy mode, aka its gonna try to match as FEW occurrences of the 'a' as possible.

### Look-ahead and Look-behind
Given our email expression, here's a translation. I will put the regex and section of string that corresponds to the translation in code snippets:

Regex: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

String: .....@gmail.com

/^ The beginning of the regex expression, searching from the start of the string

([a-z0-9_\.-]+) Match at least one character that's either a lowercase letter, digit, an underscore, period, or a hyphen Youareawesome This would be the first part of the email

@ Match an at symbol '@'

([\da-z\.-]+) Match at least one character that's either a digit (\d is shorthand for 0-9), lowercase letter, period, or a hyphen gmail This would be the websites name

\. Match a period '.'

([a-z\.]{2,6}) Match between 2 and 6 characters that are either a lowercase letter, or a period
com This would be the domain part of the website, hence why we only want to check for 2-6 chars

$/ The end of the regex expression, ending the search at the end of the string

Hopefully after this tutorial that expression and this translation should make a lot more sense!

The main expressions are compelled to be what you have defined them to be when you use lookaheads and lookbehinds. It will not be accepted as a valid input if it is not exactly what it is.

### Author
My name is Robbin Collins. I'm currenly enrolled as a student at UT Austin's Full Stack Developer Bootcamp. 




