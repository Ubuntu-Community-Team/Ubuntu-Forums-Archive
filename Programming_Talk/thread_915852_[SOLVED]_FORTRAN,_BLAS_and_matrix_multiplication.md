---
title: "[SOLVED] FORTRAN, BLAS and matrix multiplication"
date: 2008-09-10
forum: Programming Talk
---

### Post by nsa_767 on 2008-09-10
Hi,

I am starting to feel really stupid, but I can't figure out how to use BLAS to multiply a matrix by a vector... I wrote the following Fortran code:

```

      REAL*8 X(2, 3) /1.D0, 2.D0, 3.D0, 4.D0, 5.D0, 6.D0/
      REAL*8 Y(3) /2.D0, 2.D0, 2.D0/
      REAL*8 Z(2)
      CALL DGEMV('N', 2, 3, 1.D0, X, 2, Y, 1, 0.D0, Z, 1)
      PRINT *, Z
      STOP
      END

```

DGEMV is a routine from BLAS, which should calculate Z=(0)*Z + (1)*X*Y...

Compiling the above and linking to BLAS,

```
g77 test.f -o3 -lblas
```

and then running it, produces:

```
7.63918485E-313  1.01855798E-312
```

Which is wrong since the answer should be, 18 and 24???

Any help would be much appreciated!

---

### Post by WW on 2008-09-10
I don't see anything obviously wrong.  Your example worked fine for me, on computer running gutsy with g77 and the refblas3-* packages, and on a Mac with blas compiled from source using gfortran.

How did you install blas?  From a package, or from source?  If from source, did you use g77 to build the library?

---

### Post by nsa_767 on 2008-09-10
Hmmm, my memory is somewhat hazy. I know that I didn't compile it... I did install, from the repos, LAPACK and ATLAS, both of which should (I think) install BLAS... My compiler also doesn't complain about the library being missing, so it must be there.

---

### Post by WW on 2008-09-10
Try compiling with **gfortran** instead of g77.

---

### Post by nsa_767 on 2008-09-10
OK, no change when I do that, but when I compile with -llapack instead of -lblas it suddenly spits out the right answer...

Odd, maybe BLAS isn't correctly installed on my system. Anyway, LAPACK works (even with g77), so I am happy (for now).

Thank you for your help... Any further ideas, please post them. (I am not a programmer, just a statistician needing to code something...)

---

### Post by jgte on 2008-12-03
This sort of thing happens when you specify the wrong kind (the 8 in 'real(8)' or 'real*8') of your (input or output) variables. Try another kind. Probably the default kind in BLAS is not 8.

---

