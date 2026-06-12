---
title: "Python: interrupt a command if it takes too long?"
date: 2006-01-27
forum: Programming Talk
---

### Post by veraction on 2006-01-27
I have a python program which utilizes another program (coded in C) to factorize numbers.

It uses the commands.getoutput() to run the program.

Basically, I want it to run the C program for a series of values, but if the command takes > X seconds, then it should interrupt it.

Any ideas on how I'd implement this?

edit: I'd rather not mess with the C code, but I suppose I could if I had to

---

