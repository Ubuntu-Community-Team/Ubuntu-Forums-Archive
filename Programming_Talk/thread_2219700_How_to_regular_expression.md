---
title: "How to: regular expression"
date: 2014-04-25
forum: Programming Talk
---

### Post by khatkarrohit on 2014-04-25
I was reading Regular expression in JavaScript. Regular expresion are just patterns used to match or find character combinations in strings. I am confused with some of them. 

[TABLE="class: fullwidth-table"]
[TR]
[TD][(x)]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#special-capturing-parentheses")[/TD]
[TD]     Matches 'x' and remembers the match, as the following example shows. The parentheses are called *capturing parentheses*.
     
     The '(foo)' and '(bar)' in the pattern /(foo) (bar) \1 \2/ match and remember the first two words in the string "foo bar foo bar". The \1 and \2 in the pattern match the string's last two words. Note that \1, \2, \n are used in the matching part of the regex. In the replacement part of a regex the syntax $1, $2, $n must be used, e.g.: 'bar foo'.replace( /(...) (...)/, '$2 $1' ).[/TD]
[/TR]
[TR]
[TD][(?: x)]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#special-non-capturing-parentheses")
[/TD]
[TD]Matches 'x' but does not remember the match. The parentheses are called *non-capturing parentheses*, and let you define subexpressions for regular expression operators to work with. Consider the sample expression /(?:foo){1,2}/. Without the non-capturing parentheses, the {1,2} characters would apply only to the last 'o' in 'foo'. With the non-capturing parentheses, the {1,2} applies to the entire word 'foo'.
[/TD]
[/TR]
[TR]
[TD][x(?=y)]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#special-lookahead")[/TD]
[TD]     Matches 'x' only if 'x' is followed by 'y'. This is called a lookahead.

     For example, /Jack(?=Sprat)/ matches 'Jack' only if it is followed by 'Sprat'. /Jack(?=Sprat|Frost)/ matches 'Jack' only if it is followed by 'Sprat' or 'Frost'. However, neither 'Sprat' nor 'Frost' is part of the match results.[/TD]
[/TR]
[TR]
[TD][x(?!y)]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#special-negated-look-ahead")[/TD]
[TD]     Matches 'x' only if 'x' is not followed by 'y'. This is called a negated lookahead.
     For example, /\d+(?!\.)/ matches a number only if it is not followed by a decimal point. The regular expression /\d+(?!\.)/.exec("3.141") matches '141' but not '3.141'.
[/TD]
[/TR]
[/TABLE]

Confusion is why it says (X) act as [memory device]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions") and also its explanation does not get into my head. Please explain me whats going on in the first regular expression and its example.

---

### Post by Vaphell on 2014-04-25
when you have pattern (X)(Y)\1\2 first () is assigned to \1, second to \2, thus the regex "remembers" what it matched. That means you can reuse matched chunks down the road using these positional placeholders to get XYXY patterns.

```
$ echo $'abab\nabec\nabcd'
abab
abec
abcd
$ echo $'abab\nabec\nabcd' | grep -P '([ae])([bc])([ae])([bc])'
abab
abec
$ echo $'abab\nabec\nabcd' | grep -P '[COLOR="#0000FF"]([ae])[/COLOR][COLOR="#008000"]([bc])[/COLOR][COLOR="#0000FF"]\1[/COLOR][COLOR="#008000"]\2[/COLOR]'
abab
```


'abec' line stopped matching the regex because once the parentheses matched 'a' and 'b', they locked the values of \1 and \2 to 'a' and 'b'. This is useful to match exact repetitions.

another example: match words that end with the same char they start with
```
$ echo $'aura\ntort\nlol\nwart'
aura
tort
lol
wart
$ echo $'aura\ntort\nlol\nwart' | grep -P '^[COLOR="#0000FF"](.)[/COLOR].+[COLOR="#0000FF"]\1[/COLOR]$'
aura
tort
lol
```

---

### Post by khatkarrohit on 2014-04-26
Thank you very much...this is what I need..now i will do a some practice on regular expressions...

---

