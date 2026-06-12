---
title: "BLAS/LAPACK c++ tutorial/reference?"
date: 2011-04-27
forum: Programming Talk
---

### Post by azzamite on 2011-04-27
Hi there

Anyone knows of a good c++ tutorial for blas or lapack?

Most stuff out there is for fortran, not even have I been able to find something useful for C.

I haven't found a good reference manual (something like python's or wx's), this guys explain [_how_]("http://www.netlib.org/lapack/lug/node103.html") it works but not how to use the libraries, and that [_ancient_]("http://www.netlib.org/lapack/lug/node152.html") pre 1990 naming convention they use doesn't make any sense to me at all.

In resume, I'm looking a quick and dirty tutorial for doing matrix computation using only the blas/lapack packages available in the repos from c++ (matrix, vector declaration, inverse, LU, products, etc.), I just don't care how they do it, that's what linear algebra textbooks are for right?

Hope you can help me

---

### Post by odnokamuskin on 2011-11-20
I am interested in this package too. All I have found today is [a link]("http://sourceforge.net/projects/lpp/") to Lapack++ --- C and C++ interface to the LAPACK library. However I haven't installed it yet.

I've also found different package with (probably) the same functionality, written in C++: [TNT/JAMA]("http://math.nist.gov/tnt/").

I'm curious if you have found something or not.

---

### Post by 3Miro on 2011-11-21
You will be running into some trouble with code written in FORTRAN and interfacing to it from C or C++.

Example 1: BLAS called from within C, you should be able to compile this with -lblas
```
#include <stdio.h>

// FORTRAN adds _ after all the function names 
// and all variables are called by reference
double ddot_( const int *N, const double *a, const int *inca, const double *b, const int *incb );

int main( int argc, char** argv ){
  // you can define the arrays in one of two ways
  // on the heap
  double *a = (double*) malloc( 3 * sizeof(double) );
  a[0] = 1.0; a[1] = 2.0; a[2] = 3.0;
  // on the stack
  double b[3] = { 4.0, 5.0, 6.0 };

  int N = 3, one = 1; // one really doesn't look good in C

  double dot_product = ddot_( &N, a, &one, b, &one );
  printf(" The dot product is: %f \n",dot_product );

  return 0;
};

```

Example 2: BLAS called from within C with a custom interface, you should be able to compile this with -lblas
```
#include <stdio.h>

// FORTRAN adds _ after all the function names 
// and all variables are called by reference
double ddot_( const int *N, const double *a, const int *inca, const double *b, const int *incb );

double ddot( int N, double *a, int inca, double *b, int incb ){
  return ddot_( &N, a, &inca, b, &incb );
};

int main( int argc, char** argv ){
  // you can define the arrays in one of two ways
  // on the heap
  double *a = (double*) malloc( 3 * sizeof(double) );
  a[0] = 1.0; a[1] = 2.0; a[2] = 3.0;
  // on the stack
  double b[3] = { 4.0, 5.0, 6.0 };

  double dot_product = ddot( 3, a, 1, b, 1 );
  printf(" The dot product is: %f \n",dot_product );

  return 0;
};

```


Example 3: BLAS called from within C++ with a custom interface, you should be able to compile this with -lblas
```
#include <iostream>

using namespace std;

// C++ calls functions in a different way, so you need to change specify that this is a C/FORTRAN function call

extern "C"{
// FORTRAN adds _ after all the function names 
// and all variables are called by reference
double ddot_( const int *N, const double *a, const int *inca, const double *b, const int *incb );
}

double ddot( int N, double *a, int inca, double *b, int incb ){
  return ddot_( &N, a, &inca, b, &incb );
};

int main( int argc, char** argv ){
  // you can define the arrays in one of two ways
  // on the heap
  double *a = new double[3];
  a[0] = 1.0; a[1] = 2.0; a[2] = 3.0;
  // on the stack
  double b[3] = { 4.0, 5.0, 6.0 };

  double dot_product = ddot( 3, a, 1, b, 1 );
  cout <<" The dot product is: " <<  dot_product << endl;

  return 0;
};

```


There exists a standard called CBLAS, which creates an interface between BLAS and C. This isn't always available and isn't that widely used, but here is an example.

Example 4: CBLAS called from within C, you should be able to compile this with -lcblas (assuming you have cblas installed)
```
#include <stdio.h>
#include <cblas.h>

int main( int argc, char** argv ){
  // you can define the arrays in one of two ways
  // on the heap
  double *a = (double*) malloc( 3 * sizeof(double) );
  a[0] = 1.0; a[1] = 2.0; a[2] = 3.0;
  // on the stack
  double b[3] = { 4.0, 5.0, 6.0 };

  double dot_product = cblas_ddot( 3, a, 1, b, 1 );
  printf(" The dot product is: %f \n",dot_product );

  return 0;
};

```


If you have an AMD CPU, you should get ACML form them (it is free as in no money, but it is not free as in freedom). ACML is optimized BLAS and LAPACK specially done for AMD CPUs. They also have what I call "sane" interface for C.

Example 5: ACML called from within C, you should be able to compile this with -lacml -lacml_mv (assuming you have acml installed and all the paths set)
```
#include <stdio.h>
#include <acml.h>

int main( int argc, char** argv ){
  // you can define the arrays in one of two ways
  // on the heap
  double *a = (double*) malloc( 3 * sizeof(double) );
  a[0] = 1.0; a[1] = 2.0; a[2] = 3.0;
  // on the stack
  double b[3] = { 4.0, 5.0, 6.0 };

  double dot_product = ddot( 3, a, 1, b, 1 );
  printf(" The dot product is: %f \n",dot_product );

  return 0;
};

```
NOTE: if you have ACML installed, you can use the code in Examples 1 - 3 and compile it with "-lacml -lacml_mv" instead of "-lblas" and it will work just fine. 

Intel has their MKL library, however, it is not free. Also, I think MKL only comes with the standard BLAS interface, which means that you will have to use the code form Examples 1 - 3.

LAPACK works the same way as BLAS. It is a separate library so you need to compile with "-llapack -lblas" (or just "-lacml -lacml_mv" or "-lmkl"), but the interface to it is the same.

---

### Post by Dirich on 2011-11-22
A few things to keep in mind when using blas and lapack:


[LIST=1]
[*] in the compiler use -lblas and -llapack to link the libraries. If you are on ubuntu 11.10 put them after the files that call the routines
[*]use the fortran routines as the C one are the automatic translation done by a program so they are not as good as the fortran ones (which you can find in optimized version by downloading the ATLAS or GOTO blas)
[*]anything must be passed by reference and not by value (as you have seen from the previous poster, the value one is passed by initializing a variable to one and passing its address)
[*]fortran saves row wise, C too but it saves array of multiple dimensions as array of arrays, which means that a bidimensional matrix nxn is saved COLUMN wise. For performance you can not copy the matrices every time and pass their transpose, so you should write everything in a monodimensional array and use macros to handle them as if they were bidimensional.
[*]when you use a fortran routine in c you must declare it with the original fortran name followed by a "_". Like dgemm_(...)
[/LIST]

That's pretty much everything that I had to deal with when I started using BLAS/LAPACK.
If you find something strange about the dimension (LEADING dimension), that means they are thinking about non-square matrices. I don't deal with those, if you do neither, just slap there the dimension of your matrices without worrying.

Pretty much the previous poster explained point 1, 3 and 5, even if 5 is a bit implicit.

---

### Post by lehn on 2012-09-02
I hope the original poster has been able to successfully use LAPACK.

Wether a matrix is square or rectangular has nothing to do with the leading dimension.  The leading dimension is necessary if you are dealing with sub-matrices.

Just consider a 3x3 matrix.  When you allocate it then you will allocate memory for 9 elements, right?  So you can allocate these elements such that they are contiguously in memory, e.g. row-wise

a11, a12, a13, a21, a22, a23, a31, a32, a33

Now assume you want to operate on a sub-matrix that consists of the last two columns.  Then you are interested only in these elements ( I cross out the other with X):

X, a12, a13, X, a22, a23, x, a32, a33

You see that the rows of this sub-matrix are still contiguously in memory:

first row is a12, a13
second row is a22, a23
third row is a32, a33

But each of this "row blocks" is separated from the next by 3.  This is the leading dimension, i.e. the leading dimension is 3, which is the number of  columns of the "mother matrix".

The formal definition of the leading dimension for a matrix in row-major format is the distance between elements in the same column.  In the above example the distance in memory between a12 and a22 is 3,...


The following was written as documentation for my numerical C++ library "FLENS".  But it also gives a general overview of the BLAS/LAPACK concepts:

[http://www.mathematik.uni-ulm.de/~lehn/flensdoc.pdf](http://www.mathematik.uni-ulm.de/~lehn/flensdoc.pdf)


And here the link to the library itself

[http://www.mathematik.uni-ulm.de/~lehn/FLENS/index.html](http://www.mathematik.uni-ulm.de/~lehn/FLENS/index.html)

Among other things you can do with it: It makes it pretty trivial to use LAPACK from within you C++ program.

---

