---
title: "Automatically installed libraries have the wrong name?"
date: 2008-11-16
forum: Packaging and Compiling Programs
---

### Post by MarcusAntonius on 2008-11-16
Hi everybody,

I am using Ibex and I have to compile a program which needs to link fortran with C files (at least I think so). Therefore I installed libg2c and libgfortran. In the Makefile I tried the options -lg2c or -lgfortran, but both times the linker (ld) complained that he couldn't find these libraries (in Hardy this problem never occured). So I looked into /usr/lib/ and found the files including the links (libgfortran.so.3 -> /usr/lib/libgfortran.so.3.0.0) and (libg2c.so.0 -> libg2c.so.0.0.0) when I created the same links, but called libgfortran.so and libg2c.so ld worked without any problems.

In Hardy these links have been created automatically I think. Is this a bug or do I get something wrong?

I posted this issue some time ago in Programming talk, which was probably the wrong place, and I didn't get any replies. Therefore I repost it here.

---

