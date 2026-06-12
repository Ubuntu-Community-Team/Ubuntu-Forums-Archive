---
title: "c++ and linear algebra"
date: 2007-12-27
forum: Programming Talk
---

### Post by jeremytaylor on 2007-12-27
Hi,
I do a lot of numerical/computational linear algebra and until now I have relied on fortran90/95 and BLAS/LAPACK/Scalapack. However I'm currently trying to tackle a problem that would benefit from some object oriented goodness and so would like to code it in C++. Does anyone have any recommendations for linear algebra packages for c++? I have tried google and there seem to be a wealth of options but I'm unsure which to pick.

Any advice would be much appreciated.
Jeremy

---

### Post by xtacocorex on 2007-12-27
FORTRAN can do OOP, not as elegant as C++ yet, but it is possible.

I thought LAPACK abd BLAS have C++ bindings.

---

### Post by samjh on 2007-12-27
[http://math.nist.gov/tnt/index.html](http://math.nist.gov/tnt/index.html) looks suitable.

---

### Post by thk on 2007-12-27
Take a look at the Boost uBLAS library. Not as fast as many FORTRAN implementations, but they are working on wrappers so you can have the best of both.

---

### Post by hod139 on 2007-12-28
> **xtacocorex said:**
> 
I thought LAPACK abd BLAS have C++ bindings.
The GNU Scientific library has implemented [cblas]("http://www.gnu.org/software/gsl/manual/html_node/GSL-CBLAS-Library.html"),  For lapack, there is clapack, which is simpply and f2c converstion.  There is also lapack++, which is a c++ implementation.

I would recommend you check out [atlas]("http://math-atlas.sourceforge.net/") instead of using the f2c implementations.

---

### Post by jeremytaylor on 2007-12-28
Thanks everyone, I'll have a look at those.

Fortran can do OOPish :) I've written some and it's not pretty.

Jeremy

---

