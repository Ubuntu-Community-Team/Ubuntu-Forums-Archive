---
title: "C libraries - Whats out there?"
date: 2007-02-16
forum: Programming Talk
---

### Post by raspa_sete on 2007-02-16
Hi, iv'e been programming in C, but now I need some other stuff.
My question is:

Which C libraries are out there?
(C not C++)

So far i've found:

-GSL - Gnu scientific library

-numerical recipes in C - (this is half a library)

are there more?

Thank you very much

---

### Post by lnostdal on 2007-02-16
uhm, what other stuff do you need?

try ```
sudo aptitude search \\-dev
```

---

### Post by runningwithscissors on 2007-02-17
There are C libraries available for every imaginable thing.
Except maybe high precision mathematics (or maybe I just haven't looked hard enough).

---

### Post by WW on 2007-02-17
For arbitrary precision arithmetic, there is GMP: [http://www.swox.com/gmp/](http://www.swox.com/gmp/)

---

### Post by runningwithscissors on 2007-02-17
> **WW said:**
> For arbitrary precision arithmetic, there is GMP: [http://www.swox.com/gmp/](http://www.swox.com/gmp/)
Thanks. Will check them out. :)

---

### Post by raspa_sete on 2007-02-19
Thank so far people!

I am looking for C libraries with linear algebra. Specifically Singular Value decomposition and pseudo inversion algorithms.

GSL has it, but they define matrices through some structs that will force me to change a big part of my programming, and the Recipes in C, has a small program that make the indexes  of size "n" lists to go from 1 to n instead of 0 to n-1. again big changes in my stuff.

Can someone help me!

Thanks.
I've already checked the above links but haven't found what I as looking for.

---

### Post by WW on 2007-02-19
LAPACK ([http://www.netlib.org/lapack/](http://www.netlib.org/lapack/) ) is a good library for linear algebra.  For Ubuntu 6.06 (dapper),  install the packages **lapack3** and **lapack3-dev**. (They might be the same in Ubuntu 6.10--check by searching in Synaptic.)  It is actually a Fortran library, but it is  easily callable from C.

Here's a short C++ program that computes the eigenvalues of a 4x4 matrix with the LAPACK function DGEEV:
```

//
//  ev.cpp
//
//  This program uses the LAPACK library function DGEEV to compute the
//  eigenvalues of a 4x4 matrix.  It demonstrates calling LAPACK from C++.
//
//  To compile the program (on Ubuntu 6.06, and probably other Debian-based
//  distributions):
//     g++ ev.cpp -L/usr/lib/atlas -llapack -lblas -o ev
//

#include <iostream>

using namespace std;

//      SUBROUTINE DGEEV( JOBVL, JOBVR, N, A, LDA, WR, WI, VL, LDVL, VR,
//     $                  LDVR, WORK, LWORK, INFO )

extern "C" void dgeev_(char *jobvl, char *jobvr, int *n, double *a, int *lda,
                         double *wr, double *wi,
                         double *vl, int *ldvl, double *vr, int *ldvr,
                         double *work, int *lwork, int *info);

int main(void)
    {
    char jobvl = 'N';
    char jobvr = 'N';

    int N = 4;
    double M[16] =
        {
        1.0, 3.0, 0.0,  0.0,
        0.0, 2.0, 0.0,  0.0,
        0.0, 0.0, 3.0, -1.5,
        0.0, 0.0, 1.5,  3.0,
        };

    double wr[4];
    double wi[4];

    double vl[100];
    int ldvl = 4;
    double vr[100];
    int ldvr = 4;

    double work[100];
    int lwork = 100;

    int info;

    cout << "Calling dgeev\n";

    dgeev_(&jobvl, &jobvr, &N, M, &N, wr, wi, vl, &ldvl, vr, &ldvr, work, &lwork, &info);

    cout << "Back from dgeev\n";

    if (info == 0)
        {
        cout << "The eigenvalues are:\n";
        for (int i = 0; i < N; ++i)
            cout << wr[i] << " + " << wi[i] << "i\n";
        }  
    }

```
LAPACK also has several variations for SVD.  Check the LAPACK User's Guide.

---

### Post by hod139 on 2007-02-19
There is [ATLAS]("http://math-atlas.sourceforge.net/") (Automatically Tuned Linear Algebra Software) and [CBLAS]("http://tensor.tamu.edu/docs/cblas.html") (C interface to the FORTRAN BLAS routines).

---

### Post by raspa_sete on 2007-02-20
Man!
I can import functions from fortan?
Wish I knew that sooner.

How is it done in general?
I saw something about adding underscores to the functions name or of the sorts.
any reference?

thank

---

### Post by hod139 on 2007-02-21
Too my knowledge, people usually run the FORTRAN code through a FORTRAN-to-C converter, and link against the C code.

---

### Post by WW on 2007-02-21
The program that I gave above is only superficially a C++ program.  Here is a C version of that program, to demonstrate that you can easily call the LAPACK functions from C.  The main points to observe are that the function name has an underscore at the end (so the Fortran function DGEEV becomes dgeev_), and all the arguments are pointers (no call-by-value arguments).
```

/*
 *  evtest.c
 *
 *  This program uses the LAPACK library function DGEEV to compute the
 *  eigenvalues of a 4x4 matrix.  It demonstrates calling LAPACK from C.
 *
 *  To compile the program:
 *     gcc evtest.c -L/usr/lib/atlas -llapack -lblas -o evtest
 */

#include <stdio.h>

/*
 *      SUBROUTINE DGEEV( JOBVL, JOBVR, N, A, LDA, WR, WI, VL, LDVL, VR,
 *     $                  LDVR, WORK, LWORK, INFO )
 */

void dgeev_(char *jobvl, char *jobvr, int *n, double *a, int *lda,
                         double *wr, double *wi,
                         double *vl, int *ldvl, double *vr, int *ldvr,
                         double *work, int *lwork, int *info);

int main(void)
    {
    char jobvl = 'N';
    char jobvr = 'N';

    int N = 4;
    double M[16] =
        {
        1.0, 3.0, 0.0,  0.0,
        0.0, 2.0, 0.0,  0.0,
        0.0, 0.0, 3.0, -1.5,
        0.0, 0.0, 1.5,  3.0,
        };

    double wr[4];
    double wi[4];

    double vl[100];
    int ldvl = 4;
    double vr[100];
    int ldvr = 4;

    double work[100];
    int lwork = 100;

    int info;

    printf("Calling dgeev\n");

    dgeev_(&jobvl, &jobvr, &N, M, &N, wr, wi, vl, &ldvl, vr, &ldvr, work, &lwork, &info);

    printf("Back from dgeev\n");

    if (info == 0)
        {
        int i;
        printf("The eigenvalues are:\n");
        for (i = 0; i < N; ++i)
            printf("%8.5f + %8.5fi\n",wr[i],wi[i]);
        }  
    }

```
Compile and run:
> 
$ gcc evtest.c -L/usr/lib/atlas -llapack -lblas -o evtest
$ ./evtest
Calling dgeev
Back from dgeev
The eigenvalues are:
 3.00000 +  1.50000i
 3.00000 + -1.50000i
 2.00000 +  0.00000i
 1.00000 +  0.00000i


---

