---
title: "How to link lapack &amp; blas?"
date: 2005-09-28
forum: Programming Talk
---

### Post by kalle314 on 2005-09-28
How do I do to link the linear algebra libraries when compiling c++ code?

I would be grateful if anyone would have a makefile to show.

I have installed blas and lapack from synaptic (refblas3, refblas3-dev, lapack3, lapack3-dev), but I guess the flags I used when compiling were not sufficient, (-lblas -llapack, -lm ...), 
bacause the compiler says it cannot find neither blas.h nor lapack.h .

---

### Post by hokim on 2005-09-28
How about trying atlas3-base,atlas3-base-dev and atlas3-headers?
atlas3-headers  have  clapack.h but not  cblas.h which, I think, is missed.
But you can get cblas.h from 'sudo apt-get source atlas3-headers'

---

### Post by giggio on 2009-05-27
Using fortran you can link using the following...

First: In your program you must define the external rountines you are going to use...
for instance:
external zhegv(.......)
Second: when compiling...let's say you are using gfortran compiler... so you do:

gfortran -lblas -llapack "input file" -o "output file .x "

Note: you can use any definition of compilation that you may be used to do after the packages are linked... I put the one I am used to.

Hope it works for you!

---

