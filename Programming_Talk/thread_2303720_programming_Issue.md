---
title: "programming Issue"
date: 2015-11-21
forum: Programming Talk
---

### Post by gravor on 2015-11-21
[COLOR=#000000]Hello[/COLOR]
[COLOR=#000000]I would like to compile a fortran program but I have this message.[/COLOR]
[COLOR=#000000]Error: invalid instruction suffix for `push' [/COLOR]
[COLOR=#000000]What should I do ?


[/COLOR]

---

### Post by T.J. on 2015-11-23
That can indicate a *possible* bug in GCC.  Do you have some example code that generates the error for testing?

---

### Post by TideMan on 2015-11-24
Are you using gfortran?
If so, what do you get when you type:
gfortran -c myprogram.f90

---

