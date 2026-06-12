---
title: "Fortran problems compiling and running Siesta"
date: 2006-05-31
forum: Programming Talk
---

### Post by gt24 on 2006-05-31
Hello.  I am having issues with a program and getting support for said program called Siesta.  A coworker is not able to run it all so well, so I assisted them.  I initially tried to compile the program using the GNU Fortran compilers but ran into issues, so then I installed the Intel Fortran Compiler and that allowed for compilation.  However, to run the program you need to compile those problems.  An example problem won't compile and it should and it is calling the GNU Fortran 77 compiler.

So, what to do....  right now, I am thinking of uninstalling the GNU 77 compiler and hoping that the Intel Fortran compiler takes over.  Good plan?  Also, is anybody here even running Siesta?

---

### Post by mclaudt on 2008-09-17
Sorry, I have little to be late with response =)

I had the same problems. Main program compiles well if you follow the README in ~/siesta/Src/Sys before installation:
```

* Look for a .make file in this directory that might be appropriate for
  your particular configuration. If there is none, write your own using
  the existing files as guides.
* Copy or link the file to the Src directory, renaming it as "arch.make".

```
So the right compiler (ifort, i.e. Intel's, in my case) is using automatically.
But other programs in this package that have to be compiled separately (for example, atm) still try to use old g77.
So you have to edit manually appropriate MAKEFILE and change FC= g77 to FC= ifort.

---

