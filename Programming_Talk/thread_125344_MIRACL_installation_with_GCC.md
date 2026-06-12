---
title: "MIRACL installation with GCC?"
date: 2006-02-03
forum: Programming Talk
---

### Post by veraction on 2006-02-03
MIRACL ([http://indigo.ie/~mscott/](http://indigo.ie/~mscott/)) includes a program to factor numbers. It comes with the source, and a win32 exe file. I want to run this natively on my ubuntu box (not through wine).

So, I guess I need to install the MIRACL libraries, but I am having trouble. 

I have the instructions in the manual.ps file, but when it says to run a command, I get an error:
```
$ ls
amd64.txt    double.txt  include       makemcs.txt  msvisual.txt  SSE2.TXT
a.out        exe         itanium.txt   manual.doc   problems.txt  update.txt
arm.txt      factor.c    kcmcomba.txt  mex.c        readme.txt
borland.txt  first.txt   KCM.TXT       mex.o        smartmip.txt
config.c     float.txt   lib           miracl.lst   source
config.o     free        linux.txt     mirdef.h     sparc.txt

$ gcc -I. -c -O2 mr*.c
gcc: mr*.c: No such file or directory
gcc: no input files

```

Now there are a bunch of mr*.c files in the source directory, but if I run the command in there, I'll get 5000+ lines of errors.


So, anyone install MIRACL on ubuntu and have any hints?

---

### Post by toojays on 2006-02-03
Sorry to not have a direct answer for your question, but you may have better luck with the [GNU Multiprecision Library](http://swox.com/gmp/), which is in the Ubuntu repositories, and is Free Software.

---

### Post by veraction on 2006-02-03
Thanks for the response.

I have been using GMP for a while now, but I wanted to use MIRACL's factoring number program since it is faster than anything I could do myself manually in GMP & it is faster than GMP's Pollard Rho factor demo.

Guess it would be possible to translate it maybe, I'm not willing to invest that much time

---

