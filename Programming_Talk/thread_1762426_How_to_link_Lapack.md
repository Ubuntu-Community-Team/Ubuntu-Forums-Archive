---
title: "How to link Lapack?"
date: 2011-05-19
forum: Programming Talk
---

### Post by mmar on 2011-05-19
Hi!

I have just installed Lapack and Blas from Synaptic. I'm trying to compile this simple program:

> [B]#include <stdio.h>
#include <clapack.h>
#include <cblas.h>


void sgesv( int* n, int* nrhs, float* a, int* lda, int* ipiv, float* b, int* ldb, int* info );
                

int main()
{

[/B][B]int uno = 1;
int tres = 3;

[/B][B] float A [ ]={
2, 1, 1,
3, -1, 1,
0, 2, 3};

float x[ ]= {0, 0, 0};

float b [ ] = {1, 0, 3};

int ipiv[3];
int info;
int i;

sgesv (&tres, &uno, A, &tres, ipiv, b, &tres, &info);

for (i=0; i<3; ++i)  printf("%f\n", x[i]);

return 0;

}[/B]But I get the following error: "undefinded reference to 'sgesv'" when I type "gcc lap.c -o lap -llapack -lblas"
I wrote another program that just uses BLAS and compiles fine with "gcc prueba.c -o prueba -lblas". However, this program using the 
lapack routine returns an error. Have I missed anything? What am I doing wrong?

Thanks in advance

---

### Post by Arndt on 2011-05-19
> **mmar said:**
> Hi!

I have just installed Lapack and Blas from Synaptic. I'm trying to compile this simple program:

But I get the following error: "undefinded reference to 'sgesv'" when I type "gcc lap.c -o lap -llapack -lblas"
I wrote another program that just uses BLAS and compiles fine with "gcc prueba.c -o prueba -lblas". However, this program using the 
lapack routine returns an error. Have I missed anything? What am I doing wrong?

Thanks in advance

It seems this page is relevant: [http://www.netlib.org/clapack/faq.html](http://www.netlib.org/clapack/faq.html). So the function is called sgesv_.

---

### Post by mmar on 2011-05-19
Thank you for your help. I totally forgot the underscore because I'm using a guide for Fortran.

---

