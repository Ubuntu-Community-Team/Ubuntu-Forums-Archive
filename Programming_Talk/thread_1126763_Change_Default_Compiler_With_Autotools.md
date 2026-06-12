---
title: "Change Default Compiler With Autotools?"
date: 2009-04-15
forum: Programming Talk
---

### Post by jsmidt on 2009-04-15
I have written a program in C and have successful used autotools to generate a Makefile that works.

However, the code compiles using gcc. (This is usually a good thing.)  However, my collaborators would like the code to use the intel compilers to give the code some major speed boosts.  The intel c compiler is icc.

Is there a way to make autotools default to the intel compiler?  Do I alter AC_PROG_CC in configure.ac in some way?  Thanks.

---

