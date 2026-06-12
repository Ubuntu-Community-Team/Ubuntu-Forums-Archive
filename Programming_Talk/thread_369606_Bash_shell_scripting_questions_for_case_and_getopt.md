---
title: "Bash shell scripting questions for case and getopts."
date: 2007-02-24
forum: Programming Talk
---

### Post by AsGF2MX on 2007-02-24
Question 1:
How can I use the case statement on a range?
I've tried {0..10} {11..100} to no avail.

Question 2:
I use get opts to take arguments and I now have a need for one of the options to take multiple parameters

eg mycomm -x "Please" "Work" "Finally"

I'd really appreciate if someone can answer these two questions as google did little for me.

---

### Post by AsGF2MX on 2007-02-25
nobody?

---

### Post by Arndt on 2007-02-26
> **AsGF2MX said:**
> Question 1:
How can I use the case statement on a range?
I've tried {0..10} {11..100} to no avail.


The man page says that the patterns in 'case' are subject to pathname expansion, but the {0..10} thing (sequence expression) is not a part of pathname expansion. I suppose it could have been, but it isn't.

Generating what 'case' wants (a list separated with | characters) and putting it in a variable doesn't work, because the value of the variable will be taken as a literal string to match.

The best I can come up with right now, without resorting to Perl or something similar, is to first transform your sequence expression into a regular expression (using 'sed', for example), and then send it to 'expr' for doing the matching.

> 
Question 2:
I use get opts to take arguments and I now have a need for one of the options to take multiple parameters

eg mycomm -x "Please" "Work" "Finally"



There are programs that do work this way, but the traditional way to give arguments either has  no arguments to an option, one argument to an option, or treats all remaining arguments the same. If one option takes an arbitrary number of arguments (up to the next option), there is no way to give it an argument starting with a hyphen.

One way to keep with the tradition is to give the three strings as a list anyway, if there is a separator you can use (if not comma, then perhaps newline):

```
mycomm -x "Please,Work,Finally"
```

Another is to accept multiple uses of -x:

```
mycomm -x "Please" -x "Work" -x "Finally"
```

---

### Post by AsGF2MX on 2007-02-26
Thanks arndt. I went with the multiflag/option method you quoted and as for the comparisons, I needed about 5 ranges...cheated and used a nested if. ( $x -ge 1 ...)   :lolflag: 

The way you mentioned it would work but I think a typing out a bit more clearly would make it a lot easier to see what is what.

---

