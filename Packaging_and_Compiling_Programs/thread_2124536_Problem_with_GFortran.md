---
title: "Problem with GFortran"
date: 2013-03-11
forum: Packaging and Compiling Programs
---

### Post by lordfkiller on 2013-03-11
I am trying to compile a program that was written for Fortran 77. Apparently g77 is now obsolete and what I understand is that GFortran should be able to compile codes written for 77 (because 95 is backward compatible). However I am getting this error when trying to compile it. Here's what I do: according to program readme file, I run its configure script first, which asks for Fortran compiler path and I give it. Then the configure script runs successfully. After that I run 'make' and I get the error. I tried this with GCC and GFortran (I know GCC eventually calls gfortran)

[INDENT]date.o: In function `date_':
date.f:(.text+0x20): undefined reference to `fdate_'
collect2: error: ld returned 1 exit status
make: *** [snob] Error 1
[/INDENT]

Thanks!

---

