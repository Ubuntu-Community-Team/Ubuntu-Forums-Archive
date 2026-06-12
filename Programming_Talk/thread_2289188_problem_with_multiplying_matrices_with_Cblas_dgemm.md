---
title: "problem with multiplying matrices with Cblas_dgemm"
date: 2015-08-02
forum: Programming Talk
---

### Post by jsud on 2015-08-02
Hello,

I am writing a code in C to do matrix multiplication using cblas_dgemm function . I am dynamically allocating my matrices like this:

```

double **A= malloc(row*sizeof(double*));
for(i=0;i<row;i++)
    A[i]=malloc(column*sizeof(double));

```

the problem is that when I want to multiply using cblas_dgemm function like this:

```

cblas_dgemm(CblasRowMajor , CblasNoTrans, CblasNoTrans, m , n , k, 1.0, A, k, B, n, 0.0, C, n);

```

i'll end up with pointer type incompatibility. but when I write it this way :

```

cblas_dgemm(CblasRowMajor , CblasNoTrans, CblasNoTrans, m , n , k, 1.0, *A, k, *B, n, 0.0, *C, n);

```

it will compile without errors but the result is incorrect.

the only way I got correct results is when I use the static memory allocation of the matrix like this:

```

douoble A[r][c];

cblas_dgemm(CblasRowMajor , CblasNoTrans, CblasNoTrans, m , n , k, 1.0, *A, k, *B, n, 0.0, *C, n);

```

however this way won't work when I use large matrix sizes which is a must in what I'm doing. (it will cause a segmentation fault when I use size like 1000X1000)

does anybody knows how to solve this issue???

Thank you in advance..

---

### Post by steeldriver on 2015-08-02
I think that when we talk about a "row major array" in C/C++, we mean a 1-D object

```

double *A;

```

in which the elements are arranged *as though they are taken from successive rows of* a 2-D matrix, i.e.

```

[a11 a12 a13 a21 a22 a23 a31 a32 a33]

```

for example. You'd then dynamically allocate memory in a single-shot (not a loop)

```

A = (double *) malloc( row * column * sizeof(double) );

```

This will give 'A' the correct type (pointer-to-double rather than pointer-to-pointer-to-double) for your dgemm function prototype.

Hope this helps - you may find the example at [Multiplying Matrices Using dgemm]("https://software.intel.com/en-us/node/429920") useful (although it uses Intel MKL - you will need to replace the <mkl.h> header with the <cblas.h> one, and convert the mkl_malloc() and mkl_free() calls to their regular malloc() and free() equivalents).

FYI there's a nice discussion of row-major (C) versus column-major (Fortran) conventions in the [FFTW documentation]("http://www.cs.berkeley.edu/~fateman/papers/fftw3.pdf") (section 3.2 "Multi-dimensional Array Format").

You may also find this discussion interesting [Using BLAS from C with row major data]("http://www.christophlassner.de/using-blas-from-c-with-row-major-data.html")

---

