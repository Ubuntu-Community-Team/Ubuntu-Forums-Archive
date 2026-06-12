---
title: "Is this Fortran Source? And how to compile it for Windows?"
date: 2009-01-28
forum: Programming Talk
---

### Post by FSani on 2009-01-28
Hi all,

I apologize if this question may seem a little silly but I am searched all over and still have no answer.

I need to somehow generate an executable for windows from the source files available in this package:

[ftp://ftp.polymtl.ca/pub/nucl/dragon/dragon-3.05/DRAGON305F.TGZ](ftp://ftp.polymtl.ca/pub/nucl/dragon/dragon-3.05/DRAGON305F.TGZ)

I used Cygwin (in Windows) and as per the instruction of the Readme.txt file of the program linked above I can ./instdrag and Cygwin somehow generated an executable (.exe)

The problem here is that the executable will run only if the cygwin1.dll is in the same folder. Also when I actually run my code with an input file it doesnt complete succesfully and says Kernell error.

I know it is possible to compile this program into a windows executable (single file) but I have had no luck.

I appreciate your help,

Thanks
FS

---

### Post by ssam on 2009-01-28
```

*DECK AFERF
      FUNCTION AFERF (XX)
C
C-----------------------------------------------------------------------
C
C ERROR FUNCTION.
C
C-----------------------------------------------------------------------
C
      IMPLICIT NONE
C----
C FUNCTION
C----
      REAL  AFERF
C----
C VARIABLES
C----
      REAL     A0,A1,A2,A3,A4,A5,A6,B0,B1,B2,B3,
     &         B4,B5,B6,B7,D1,D2,X,XX,Z,Y
      INTEGER  IS
C----
      DATA A0 / 0.12837912 /, A1 / -0.37612384 /, A2 / 0.11281417 /
     1 ,   A3 / -0.26782287E-01 /, A4 / 0.50805667E-02 /
     2 ,   A5 / -0.72514300E-03 /, A6 / 0.58167427E-04 /
     3 ,   B0 /  0.39141751E-02 /, B1 / -0.17582889E-01 /
     4 ,   B2 /  0.35873539E-01 /, B3 / -0.42869095E-01 /
     5 ,   B4 /  0.32161925E-01 /, B5 / -0.11846550E-01 /
     6 ,   B6 /  0.30705572E-02 /, B7 /  0.59813837E-02 /
     7 ,   D1,D2 / 1.317, 2.040001 /
C
      X=XX
      IF (X.GE.0.) THEN
         IS=2
      ELSE
         IS=1
         X=-X
      ENDIF
      IF (X.GT.D1) GO TO 8
      Z=X*X
      Y=(((((A6*Z+A5)*Z+A4)*Z+A3)*Z+A2)*Z+A1)*Z+A0
      Y=X*Y+X
      GO TO 6

```

that's fortran.

probably fortran77 or older because it is using the fixed columns style (the first 6 characters on a line are for things like line numbers, and starting a comment with a 'c'), this a legacy from using punch cards.

have a read of [http://en.wikipedia.org/wiki/Fortran](http://en.wikipedia.org/wiki/Fortran)

on linux i use gfortran. there is also g77 which has been dropped from recent versions of GCC and ubuntu. i am not sure how you would seal with fortran on windows.

---

### Post by Zugzwang on 2009-01-28
> **FSani said:**
> 
The problem here is that the executable will run only if the cygwin1.dll is in the same folder. 

Erm, where's the problem here? You can easily assure that.

> **FSani said:**
> 
Also when I actually run my code with an input file it doesnt complete succesfully and says Kernell error.


What is the precise error? It's likely not to be "Kernell error".

---

### Post by FSani on 2009-01-28
I appreciate the comments so far. 

I do not have a problem with running it with the dll in the folder, although I would prefer to somehow compile it all together into a single exe.

The error is in the output file of the program.
! CLEPIL: ERROR CODE IN >> CLELOG       << ERROR NUMBER ( 437)
* KERNEL: COMPILING _MAIN.c2m FILE (ERROR CODE)                         IRC= 437
->@ERROR FROM KERNEL IN DRAGON CODE =          0
 DRAGON: KERNEL ERROR
 DESTROY DA FILE = _FIL001       UNIT =         99

 ABORT REQUESTED.



This error should not occur and the last line should read, Completed Successfully etc.

I do not get this error with the same version of the program that I received as an .exe (runs standalone) from a colleague.  And obviously we do not know how it was compiled.

Thanks again,

FS

---

