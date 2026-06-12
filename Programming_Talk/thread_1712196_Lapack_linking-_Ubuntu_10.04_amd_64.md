---
title: "Lapack linking- Ubuntu 10.04 amd 64"
date: 2011-03-22
forum: Programming Talk
---

### Post by jsilvav on 2011-03-22
Hi all,

I am trying to compile a code with gfortran on Ubuntu 10.04 amd 64. This code uses lapack libraries (eqrt2s)

I used the command

gfortran -llapack -lblas kondo.f90 -o k.exe

It gave me :

/tmp/ccCUAYBA.o: In function `lanczos_':
kondo.f90:(.text+0xcbf6): undefined reference to `eqrt2s_'
collect2: ld returned 1 exit status


Does anyone have any idea about this?

Thanks

J. Silva

---

