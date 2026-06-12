---
title: "Wrong gcc search path"
date: 2008-09-17
forum: Packaging and Compiling Programs
---

### Post by Strab on 2008-09-17
Hello,

Since I have switched to Hardy (a week or two ago), I am having trouble compiling a program that was compiling fine before.

The first error message I get at compilation is:
   error: stddef.h: No such file or directory

From my understanding, this file should be taken at /usr/lib/gcc/i486-linux-gnu/4.2.3/include, but when I run:
   gcc -print-search-dirs

I can see it is looking at /usr/lib/gcc/i486-linux-gnu/4.2.3/: the "include" part is missing.
I have no idea where this issue comes from and how I could solve it.

I have also gcc-4.1 installed, but -print-search-dirs gives a similar output, though the headers are also located in "include".

I have tried to reinstall gcc, gcc-4.2, g++, build-essentials, it didn't have any effect.

Does anyone have a solution or a clue?

Thanks for your help,
Strab

---

