---
title: "Linking lapack"
date: 2014-11-13
forum: Packaging and Compiling Programs
---

### Post by kweemstra on 2014-11-13
Hi all,

I have a brief question. I have a fortran (.F90) code that contains a call to the subroutine GESV.
My OS is Ubuntu 14.04 LTS, which, by default, has the lapack (shared objects) libraries placed under /usr/lib/lapack/.
I compile my code with gfortran and use the options "-L/usr/lib/lapack/ -llapack" (among others). 
The compiler doesn't complain about the linking, but it doesn't recognize the subroutine. Does anyone has a solution to this problem?

Thanks advance!
kees

---

### Post by steeldriver on 2014-11-13
Hello and welcome to the forums

Can you provide more details - for example the complete gfortran command line and the exact error message that results? in what way doesn't it "recognize" the subroutine?

I have very limited experience with gfortran - but will try to help if I can

---

### Post by alikazmi on 2014-12-09
Please provide exact information what type of error you are getting I will must resolve it.

---

### Post by dheemanth2 on 2015-07-27
How to link lapack with fortran subroutine files. Can you say how to execute .f files clearly. For example zggev.f which is available in google

---

