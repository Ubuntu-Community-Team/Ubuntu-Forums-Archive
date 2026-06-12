---
title: "bash vs. perl regular expressions"
date: 2011-07-30
forum: Programming Talk
---

### Post by donsy on 2011-07-30
I'm more used to perl-style re's so I'm a bit confused about why if at the command line I issue ```
echo [ab]* 
``` it will expand to all the filenames beginning with a or b, but if I issue just ```
echo [ab]
``` it will only echo back the literal '[ab]'. According to the manual ([click here]("http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion")), bash should regard the [ab] as a regular expression when it sees the '[' character. Why is the quantifier needed?

---

### Post by Reiger on 2011-07-30
You are not working with regular expressions in bash, or any POSIX sh for that matter. You are working with glob patterns which look similar but crucially behave very differently.

* is not “zero or more occurrences”, but it is “anything” (including nothing).
[ab] is therefore a or b.
[ab]* is therefore any file name which starts with either a or b.

Incidentally, ? is not “one or zero” but “any single character”. So [ab]? would be any file name exactly two characters long, starting with a or b.

---

### Post by Arndt on 2011-07-30
> **donsy said:**
> I'm more used to perl-style re's so I'm a bit confused about why if at the command line I issue ```
echo [ab]* 
``` it will expand to all the filenames beginning with a or b, but if I issue just ```
echo [ab]
``` it will only echo back the literal '[ab]'. According to the manual ([click here]("http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion")), bash should regard the [ab] as a regular expression when it sees the '[' character. Why is the quantifier needed?

If a file pattern doesn't match anything, bash will just leave it as it is. Since you don't have a file named "a" or "b", you get the observed result.

If you create a file named "a" and try again, you will see it producing "a".

I think this behaviour can be controlled by some variable in bash, so that you get the empty string instead when it doesn't match.

---

