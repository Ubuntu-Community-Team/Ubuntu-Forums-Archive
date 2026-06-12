---
title: "How to link C against BLAS?"
date: 2010-08-11
forum: Programming Talk
---

### Post by jseabold on 2010-08-11
All,

My knowledge of compiled languages is small.  I spend most of my time in Python.  Python is too slow for my recent needs, so I am trying to write a loop in C that calls BLAS's dgemm.  I cribbed a C++ example from [http://matrixprogramming.com/2008/01/matrixmultiply](http://matrixprogramming.com/2008/01/matrixmultiply).  The problem is that I can't get it to link against BLAS.  

```

$ gcc --version
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ ls /usr/include/cblas.h
/usr/include/cblas.h

```

Here is my code.  There may be other lurking errors still.


[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <cblas.h>
#include <time.h>

//using namespace::std;

int main(int argc, char* argv[])
{
	if (argc < 2)
	{
		printf("Usage: mm dim1 dim2 dim3\n");
		printf("Please specify matrix dimensions\n");
		return 1;
	}
	int dim1, dim2, dim3;
	dim1 = atoi(argv[1]);
	if (argc < 3)
		dim2 = dim1;
	else
		dim2 = atoi(argv[2]);
	if (argc < 4)
		dim3 = dim1;
	else
		dim3 = atoi(argv[3]);
	double A[dim1][dim2], B[dim2][dim3], C[dim1][dim3];
	srand(12345);
	double maxr=RAND_MAX;
    int i,j;
	for (i = 0; i < dim1; i++)
		for (j = 0; j < dim2; j++)
			A[i][j] = rand()/maxr;
	for (i = 0; i < dim2; i++)
		for (j = 0; j < dim3; j++)
			B[i][j] = rand()/maxr;
	double alpha = 1.;
	double beta = 0.;
    double start;
    start = clock();
	cblas_dgemm(CblasColMajor, CblasNoTrans, CblasNoTrans, dim1, dim3, dim2, alpha, *A, dim1, *B, dim2, beta, *C, dim1);
	double finish = clock();
	printf("time for C(%d,%d) = A(%d,%d) B(%d,%d) is %f s\n", dim1, dim3, dim1, dim2, dim2, dim3, (finish - start)/CLOCKS_PER_SEC);
	return 0;
}
[/PHP]

I try to compile my code like so.

```

gcc -lcblas -Werror -Wall -pedantic -o usedgemm usedgemm.c -std=c99
/usr/bin/ld: cannot find -lcblas
collect2: ld returned 1 exit status

```

This is probably something simple as telling it where to look, but I haven't had any luck.  Can someone help out in the code or the compile step?

Thanks.

---

### Post by MadCow108 on 2010-08-11
do you have the blas library installed?
sudo apt-get install libblas-dev

you have to link against libblas not libcblas:
gcc -lblas ...

you can find this stuff out by e.g. looking at package contents (if installed over a package):
dpkg -c package.deb

in ubuntu the packages are in /var/cache/apt/archives/
you can also list the contents after installation in synaptic

or online e.g. here:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by jseabold on 2010-08-11
Ha.  Thanks!  I have the blas headers, built my own with ATLAS a while back, and doing -lblas instead does the trick.

---

