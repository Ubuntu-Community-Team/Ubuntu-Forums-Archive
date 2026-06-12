---
title: "CBLAS blas.h dont compile"
date: 2007-09-04
forum: Programming Talk
---

### Post by marinko on 2007-09-04
how can i install correctly CBLAS BLAS because i can compile

---

### Post by gnusci on 2007-09-05
You first of all need to compile BLAS, download it form:

[http://www.netlib.org/blas/](http://www.netlib.org/blas/)

Here is the direct link:

[http://www.netlib.org/blas/blas.tgz](http://www.netlib.org/blas/blas.tgz)

In case does no work just go to the above webpage and look for: blas.tgz

umcompress with:

**$ tar -xvf blas.tgz **

and then move into the BLAS directory (use your home directory) and compile with:

**$ make**

After few seconds y will have your lib.

The second step is to look for the C interface for BLAS (because BLAS was written in FORTRAN it needs an interface to be used in C), which is call cblas:

[http://www.netlib.org/blas/blast-forum/cblas.tgz](http://www.netlib.org/blas/blast-forum/cblas.tgz)

if not here just give a look to the webpage again. In any case download it to your home directory and uncompress it.

move now into CBLAS and choose the symbolic link for Makefile.in, You are working with Ubuntu, so just use:

**$ ln -s Makefile.LINUX Makefile.in**

and then to get all use:

**$ make all**

now enjoy it.... :)

PS: I recommend you to check:

[http://en.wikipedia.org/wiki/LAPACK](http://en.wikipedia.org/wiki/LAPACK)
[http://en.wikipedia.org/wiki/Basic_Linear_Algebra_Subprograms](http://en.wikipedia.org/wiki/Basic_Linear_Algebra_Subprograms)
[http://www.netlib.org/lapack/](http://www.netlib.org/lapack/)

---

