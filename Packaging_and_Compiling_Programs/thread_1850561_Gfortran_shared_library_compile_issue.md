---
title: "Gfortran shared library compile issue"
date: 2011-09-26
forum: Packaging and Compiling Programs
---

### Post by jr226 on 2011-09-26
Hi All,

I'm trying to compile a FORTRAN file into a library file.  I'm using Ubuntu, and gfortran.  I've tried using 

[INDENT]gfortran -c subroutines.f90 -o subroutines.o[/INDENT]

with the intent of compiling the object file into a library.  When I compile I get a series of errors, which I think all stem from the Error: Expecting END PROGRAM statement at (1).  With a library you should only have subroutines and do not need a program, right?

Any hints on how to compile would be appreciated!

JR

---

### Post by jr226 on 2011-09-28
Figured it out, in case anyone else needs help with this:

gfortran -c -ffree-line-length-0 -o subroutines.so subroutines.f90

where -ffree-line-length-0 sets the line length limit (default ~132 for F90) to infinitie.

---

