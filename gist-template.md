# Regex For Standard Phone Numbers

Introductory paragraph (replace this with your text)

## Summary

In this gist I will go over an effective Regex for finding and match a standard 10 digit phone number.

`^\(?\d{3}\)?[\s.-]\d{3}[\s.-]\d{4}$`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

  * Anchors will match a position either before or after a set of characters and are a way to help the regex identify possible matches. " ^ " will match the
  position before the first character in the string and " $ " will match the position after the last character in the string.

  In the snippet given, `^` at the first position signifies that the match we're looking for has to start at the beginning of a string with `$` at the end to make sure it doesnt have characters following immediately after.

### Quantifiers

  * Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.
    `*` => Matches 0 or more times
    `+` => Matches 1 or more times
    `?` => Matches 0 or 1 times
    `{n}` => Matches "n" number of times
    `{n,}` => Matches at least "n" number of times
    `{n, m}` => Matches anywhere from "n" to "m" number of times

  * In the snippet given, ` {3} ` appears twice after a ` \d ` meaning that for this section, we are looking for 3 digits (\d) in a row.

### Bracket Expressions

  * There are 3 different sets of bracket expressions used to for regex.

    `[]` indicate a set of characters to match. Any individual character between the brackets will match, and you can also use a hyphen to define a set.
    `{}` are used to specify an exact amount of things to match and are used after an expression. (see Quantifiers)
    `()` represent remembered matches which especially useful for find and replace operations or any time you need to do something with part of the match.

  In the snippet given, we have `[\s.-]` appearing twice. Because phone numbers can be typed non-uniformly, it is important to incorporate various methods for spacing bewtween number sets. So this bracket expression help the regex to find either a space `\s`, a dot `.` or a hyphen `-` as a separator.

### Character Classes

  * Character Classes/Sets can be used to customize what the regex matches with by placeing the characters between `[]`.

  EX: `\d[123]\d` will tell the regex to look for a series of 3 digits where the middle digit has to either be a 1, 2, or 3. Similarly, this can be written as `\d[1-3]\d` where the character class has been written as a range to match the same result.

### The OR Operator

  * Also known as Alternation, the OR Operator is signified by a " | " or pipe character.

  EX: If we were looking through a long list of phone numbers and only wanted to find the ones with an area code in Orange County, OC has two area codes: 714 and 657. So in order to pull both area codes out of the list we would write the regex as `(714|657)` which will tell it to look for either AC 714 OR 657.

### Flags

  * Flag will modify the behavior of the regex search. `/a/` will go out and search for the literal character `a` in lowercase, however if we wanted to find any instance of `a` either lower or uppercase then we write it as `/a/i` where `i` is telling the regex to ignore casing.
  
### Character Escapes

  * Character Escapes are used when we want to use a character literally instead of as a metacharacter. If we wanted to use a `*`, `+`, or a `?` literally, we would need to escape it out of its meta meaning to use it literally in a search. In order to escape metas, they need to be prefaced with a backslash.

  In the Snippet given, Group 1 has a `\(` and `\)` where normally a `()` has a meta meaning to separate what inside the parentheses into groups, in this example it is searching for the literal `(` and `)` surrounding the area code for a phone number.
## Author

My name is Travis Alexander, I'm learning to become a full-stack web developer, always trying to better understand things today than I did yesterday. https://github.com/talexander91
