---
title: "compiling with gfortran and ifort"
date: 2010-09-14
forum: Programming Talk
---

### Post by PiresSLB on 2010-09-14
Hello I am new here and this may be an easy question:

I have a main program a.f that calls a subroutine located in b.f. However I need this subroutine to be evaluated in quadruple precision (but not a.f) and I do it by defining real(16) in b.f. What is the best way to do this? How can a.f receive a real(16) object?

I tried compiling a.f with gfortran and b.f with ifort (to support real(16) type) and linking but it creates errors like:
undefined reference to `__qtod'

If i compile both with ifort I get errors like:
forrtl: severe (174): SIGSEGV, segmentation fault occurred
Image              PC                Routine            Line        Source             
test               00000000004118EE  Unknown               Unknown  Unknown
test               0000000000403229  Unknown               Unknown  Unknown
test               000000000040312C  Unknown               Unknown  Unknown
libc.so.6          00007F3C2C8F6C4D  Unknown               Unknown  Unknown
test               0000000000403029  Unknown               Unknown  Unknown

My problem is basically that I have a.f which runs on its own and compiles fine with gfortran and double precision and also b.f which runs on its own and compiles fine with ifort and has quadruple precision with real(16). However now I need to make them talk to each other.

Has anyone any ideas how to do this?
Thanks

---

### Post by Miguel on 2010-09-14
From what little I know, you must compile both fortran sources with the same fortran compiler. I think ifort may interface with gcc, so that it won't require icc, but mixing fortran compilers is often a no-no.

---

### Post by PiresSLB on 2010-09-14
In this case how can I compile my program with the same fortran compiler but keeping some functions in it in double precision and others in quadruple precision?

I've tried with ifort but I got the following error:
forrtl: severe (174): SIGSEGV, segmentation fault occurred
Image              PC                Routine            Line        Source             
test               0000000000413B0E  Unknown               Unknown  Unknown
test               00000000004036A9  Unknown               Unknown  Unknown
test               00000000004035AC  Unknown               Unknown  Unknown
libc.so.6          00007FE30DDB3C4D  Unknown               Unknown  Unknown
test               00000000004034A9  Unknown               Unknown  Unknown

which disappears immediately if I use gfortran and double precision everywhere.

---

### Post by Miguel on 2010-09-14
If you are not using other FORTRAN libraries, my suggestion is actually compiling **both** a.f and b.f with ifort, not with gfortran. Personally, I've never used quadruple precision... and I work with scientific software day in day out.

---

### Post by PiresSLB on 2010-09-14
In my problem b.f is a very complicated calculation that can be done in double precision.  However for special values of its arguments the calculation in double precision breaks down and you start getting NaN or any answer you like. 

If I then switch to quadruple precision I recover again the expected results even when the arguments take these especial values.

So I would really like to have b.f in quadruple precision and feed the result to a.f when I am in these dangerous regions.
I did that by changing from gfortran to ifort however now I get these sort of errors:
forrtl: severe (174): SIGSEGV, segmentation fault occurred
Image              PC                Routine            Line        Source             
test               0000000000413B0E  Unknown               Unknown  Unknown
test               00000000004036A9  Unknown               Unknown  Unknown
test               00000000004035AC  Unknown               Unknown  Unknown
libc.so.6          00007FE30DDB3C4D  Unknown               Unknown  Unknown
test               00000000004034A9  Unknown               Unknown  Unknown

in the part of the computation done by a.f . That is why I am asking whether there could be a more clever way of doing this.

---

### Post by Miguel on 2010-09-14
> **PiresSLB said:**
> In my problem b.f is a very complicated calculation that can be done in double precision.  However for special values of its arguments the calculation in double precision breaks down and you start getting NaN or any answer you like. 

If I then switch to quadruple precision I recover again the expected results even when the arguments take these especial values.

So I would really like to have b.f in quadruple precision and feed the result to a.f when I am in these dangerous regions.
I did that by changing from gfortran to ifort however now I get these sort of errors:
forrtl: severe (174): SIGSEGV, segmentation fault occurred
Image              PC                Routine            Line        Source             
test               0000000000413B0E  Unknown               Unknown  Unknown
test               00000000004036A9  Unknown               Unknown  Unknown
test               00000000004035AC  Unknown               Unknown  Unknown
libc.so.6          00007FE30DDB3C4D  Unknown               Unknown  Unknown
test               00000000004034A9  Unknown               Unknown  Unknown

in the part of the computation done by a.f . That is why I am asking whether there could be a more clever way of doing this.

Are you linking a.f to any other FORTRAN library? Any other. Be it blas, atlas, lapack... anything. If you are using ifort for a single fortran file, you'll have to use it for everything.

As an intermediate solution, I've found old references saying that real*16 does not work in gfortran (or only on selected hardware), but real*10 apparently does. Would real*10 work? Yeah, I know it's a hack, but AFAIK is supported on all SSE enabled hardware.

EDIT: This may help [http://www.tek-tips.com/viewthread.cfm?qid=1527201&page=13](http://www.tek-tips.com/viewthread.cfm?qid=1527201&page=13)

---

### Post by till_hm on 2010-09-14
If you are passing variables back and forth between the libraries and you don't cast them as the correct precision (i.e. have one in double and one in quadruple) you are very likely to get segmentation faults.

---

### Post by PiresSLB on 2010-09-14
I've done part of the calculation in quadruple precision and it is stored in a real(16) variable in b.f . Is there a way I can cast (truncate) it to a real*8 variable and feed this back to a.f and continue the rest of the computation in double precision?

How do I cast from real(16) to real*8?

---

