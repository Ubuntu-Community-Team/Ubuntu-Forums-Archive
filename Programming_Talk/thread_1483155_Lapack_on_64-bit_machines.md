---
title: "Lapack on 64-bit machines"
date: 2010-05-14
forum: Programming Talk
---

### Post by paulhalks on 2010-05-14
Hello,

I'm running Ubuntu 10.04 LTS (64 bit) on an Intel Core i7 CPU, and I'm having programs with the Lapack library.

Now, I've done some programming in Fortran before, but I have virtually nill experience setting up compilers, libraries etc. so please bear with me.

I've installed both the gfortran and the ifort compilers (having followed the instructions at [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)).  So, I'm assuming I should have the latest libraries.

I've been given some code to run (author absent) and when I run it, I receive the error

/tmp/ifortoKNzRC.o: In function `MAIN__':
code.f: (.text+0x734): undefined reference to `dlamch_'
code.f: (.text+0x2c81): undefined reference to `zheevr_'


The code (apparently) works, so I'm assuming this isn't a coding problem, but a problem with how I have set up my machine / ubuntu / compilers ... Since it hasn't found the routines zheevr and dlamch.

If someone could shed some light on this problem, I would be very grateful.  If there's any obvious info I've omitted, please ask.

Thanks.

---

### Post by l_o_g on 2010-05-14
Hello,
I guess you have LAPACK and BLAS library on your computer installed and tested. Will you write here the command you use to compile your code.f and the location of LAPACK_xxx.a and BLAS_xxx.a (xxx - I have LINUX there :-) )

---

### Post by soltanis on 2010-05-14
Looks like you are missing some libraries that your code is supposed to link to. Since your code compiled through (I don't know much about Fortran but I assume it has the concept of headers), then I am guessing you just forgot to add a proper -l line to your compilation command.

I don't know anything about the library you're talking about but I do know that if I wanted to write some C code that linked to the OpenGL library, for example, I'd need to write;

```

gcc -o example -lGL example.c

```

That's "minus ell" not "minus one".

---

### Post by l_o_g on 2010-05-14
[http://www.netlib.org/lapack/](http://www.netlib.org/lapack/)
[http://www.netlib.org/blas/](http://www.netlib.org/blas/)

I compiled both and got this: blas_LINUX.a, lapack_LINUX.a, tmglib_LINUX.a
When I use LAPACK/BLAS I need to write:

gfortran -c example.f90
gfortran example.o lapack-3.2.1/lapack_LINUX.a lapack-3.2.1/blas_LINUX.a -o example

because I have lapack_LINUX.a and blas_LINUX.a in a directory lapack-3.2.1

OR you can use Synaptic to download precompiled BLAS/Lapack libraries and then you need to write:

gfortran -c example.f90
gfortran example.o -llapack -lblas -o  example

---

### Post by TheStatsMan on 2010-05-14
A related issue you should really use an optimised version of blas with lapack. There is a massive difference in performance. Have a look into atlas, which you can also simply install using synaptic or apt-get

---

### Post by mmix on 2010-05-14
[http://code.google.com/p/qmcpack/issues/detail?id=9](http://code.google.com/p/qmcpack/issues/detail?id=9)

edit:
[http://www.mail-archive.com/siesta-l@listserv.uam.es/msg03888.html](http://www.mail-archive.com/siesta-l@listserv.uam.es/msg03888.html)

---

