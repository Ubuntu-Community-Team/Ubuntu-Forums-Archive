---
title: "Fortran CODE Version?"
date: 2013-08-02
forum: Programming Talk
---

### Post by Senju on 2013-08-02
Hi All, 
I have some FORTRAN code that compiles, but gives this error in the linker, when I try to build an executable:
```
$ gfortran -Wall -o "ljewald" "ljewald.f"
/usr/lib/gcc/i686-linux-gnu/4.7/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: error: ld returned 1 exit status
```
This code has some hidden characters, and makes me think it was written in MS Word or something, That Asside,
I m not sure what version of Fortran it is in, and I am not sure how to find out. 
heres a link to the Original Code:

[nanocluster.umeche.maine.edu/ljewald.f]("http://nanocluster.umeche.maine.edu/ljewald.f")

So then, I put the code into gedit,  copied it into a new document, and this removed much of the hidden characters. This then led to errors in formating, and warnings about things like spacing. 

Then I got to thinking, is gfortran even compiling this correctly?? I think the standard gfortran uses is GNU, a superset of F95.
I see errors in things like ASSET 777,ident  which doesnt strike me as a syntax of fortran which i am familiar with. 

Can some one look at this code, and tell me what version of fortran is being used?
I am confussed by the linking errors, the hidden characters, and some other things too, so i just want to identify what version of fortran this is before I try to proceed.

---

### Post by steeldriver on 2013-08-02
[DISCLAIMER: I don't know fortran but... ] aside from the line CR terminations (which you will need to change to LF) it appears to have at least one DEC/VAX extension - the ACCEPT statements - which you will need to convert to appropriate READ statements, I think

[http://gcc.gnu.org/onlinedocs/gcc-3.3/g77/TYPE-and-ACCEPT-I-O-Statements.html#TYPE%20and%20ACCEPT%20I%2fO%20Statements](http://gcc.gnu.org/onlinedocs/gcc-3.3/g77/TYPE-and-ACCEPT-I-O-Statements.html#TYPE%20and%20ACCEPT%20I%2fO%20Statements)

I got it to compile (with warnings) after that - but obviously I don't know if it is correct since I don't know what it is or how to run it / what input it is expecting

---

### Post by ssam on 2013-08-03
I'd switch on more warnings, these will let you know if the compiler spots anything suspicious.
```
-Wextra
```
You could also try specifying the fortran version to use, eg
```
-std=legacy
```
see [http://gcc.gnu.org/onlinedocs/gfortran/Fortran-Dialect-Options.html#Fortran-Dialect-Options](http://gcc.gnu.org/onlinedocs/gfortran/Fortran-Dialect-Options.html#Fortran-Dialect-Options)

in theory fortran standards are backwards compatable, so valid fortran77 is valid fortran95 etc (though with deprication warnings).

there are also some options at [http://gcc.gnu.org/onlinedocs/gfortran/Code-Gen-Options.html](http://gcc.gnu.org/onlinedocs/gfortran/Code-Gen-Options.html) to help with code that expects specific behaviour of the compiler.

---

