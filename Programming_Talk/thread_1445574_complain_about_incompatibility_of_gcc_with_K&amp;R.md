---
title: "complain about incompatibility of gcc with K&amp;R"
date: 2010-04-02
forum: Programming Talk
---

### Post by superarthur on 2010-04-02
correct me if I am wrong
I am going through K&R really slowly (spent too much time on Pokemon Heartgold :P)
I am at section 1.9, where the code it shows create a new function called getline. I typed the code and tried compiling it and didn't work, giving "error: conflicting types for ‘getline’"
when I change all my "getline" to "getline2", it worked.
so i assume that there is a getline function already in gcc compiler

how can gcc not be compatible with the C programming bible
(I got frustrated every time I spent hours to debug my program, but solving the problem with a simple solution in the end.)

---

### Post by CptPicard on 2010-04-02
> 
man getline:

GETLINE(3)                                                          Linux Programmer's Manual                                                          GETLINE(3)

NAME
       getline, getdelim - delimited string input

SYNOPSIS
       #include <stdio.h>

       ssize_t getline(char **lineptr, size_t *n, FILE *stream);

       ssize_t getdelim(char **lineptr, size_t *n, int delim, FILE *stream);

   Feature Test Macro Requirements for glibc (see feature_test_macros(7)):

       Before glibc 2.10:
       getline(), getdelim(): _GNU_SOURCE

       Since glibc 2.10:
       getline(), getdelim(): _POSIX_C_SOURCE >= 200809 || _XOPEN_SOURCE >= 700

DESCRIPTION
       getline()  reads  an  entire  line  from  stream,  storing the address of the buffer containing the text into *lineptr.  The buffer is null-terminated and
       includes the newline character, if one was found.

...



There really is nothing in the *compiler* per se. Compiler just compiles the language. All the functions are in the standard library, or other libraries.

K&R is somewhat old... it may have some incompatibilities with modern Linux std libs.

---

### Post by dwhitney67 on 2010-04-02
> **CptPicard said:**
> 
K&R is somewhat old... it may have some incompatibilities with modern Linux std libs.

Yes, that is correct.  However if the OP wants to program identically to the K&R book, he/she could probably get away with it by specifying the -std=c89 GCC compiler flag when compiling his source code.  (not that I recommend this.)

---

### Post by rabidbadger on 2010-04-03
> **dwhitney67 said:**
> Yes, that is correct.  However if the OP wants to program identically to the K&R book, he/she could probably get away with it by specifying the -std=c89 GCC compiler flag when compiling his source code.  (not that I recommend this.)

I'm really curious to understand why you wouldn't recommend that the OP writes -- and tells his compiler to process -- standards compliant code (albeit an old, portable standard)...?

To the OP, you should also find that the command 'c89' is already aliased on your system to invoke GCC in ANSI compatible mode.

---

### Post by beradero on 2010-04-14
This works fine in FreeBSD.. I'm studing C by K&R too, and I had the same problem.. 
Exercise 1-10 is also a problem in Linux because it don't produce the ^H (backspace), but it works fine in FreeBSD (Ctrl+V Backspace produces the ^H, but in Linux the same sequence produces ^?).. So I'm using FreeBSD to do my K&R exercises..

---

