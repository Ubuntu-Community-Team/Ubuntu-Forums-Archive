---
title: "help with diff compare"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by wednesday allfather on 2008-08-28
I'm new to the use of diff.

I am trying to compare the contents of two text lists and get an output of the DIFFERENCES in the two files as a txt file.  I thought I had it figured out, but I have yet to get the correct results.  

Am I using the correct command, and if I am, what options need to be appended to this command to get the result of (contents of lines in list A)-(contents of lines of list b), where b is a subset of a (list b contains records of list a).  

I am trying to find the items not represented in the second list.  

An answer would be sufficient, but a "why" accompanying the answer would be much appreciated.  Teach a man to fish.

Thankful for any help.

---

### Post by bruce89 on 2008-08-28
I suspect you want unified diffs, which are generated using [FONT="Mono"]diff -u[/FONT]. Otherwise, the output is somewhat screwy.

---

