---
title: "CBLAS use under ubuntu"
date: 2015-07-27
forum: Packaging and Compiling Programs
---

### Post by jsud on 2015-07-27
Hello,

I'm trying to do matrix multiplication using CBLAS (of course the code is written in C language). I don't have problem with writing the code, my problem is with compiling and package installation.

while searching, a source have mentioned that I have to install BLAS and CBLAS packages... does it matter where to get them from? I mean is there specific ones for C code under Ubuntu? or not?

I've been trying to do this for weeks I'll appreciate it if someone can guide me through the process of compilation.

Thank you in advance,

jsud

---

### Post by steeldriver on 2015-07-27
Hello and welcome to the forums

AFAIK cblas is available via either the ATLAS or OpenBlas impementations

What specifically are you having trouble with? can you post a minimal code sample that demonstrates the compilation issues?

---

### Post by jsud on 2015-07-29
Hi steeldriver... thank you for replying. :)

I have been following the instructions in this link : [https://vibrationdata.wordpress.com/2011/11/07/install-cblas-in-ubuntu/](https://vibrationdata.wordpress.com/2011/11/07/install-cblas-in-ubuntu/) so, I have installed the BLAS and CBLAS packages, then I supposed to change -in the makefile- the location of "blas_LINUX.a" which I have no idea where it is. I have searched through my computer for it but didn't find it. I already have the code but still can't figure out how to compile it.
below is a simple version of my code:

**/* This code is to test matrix multiplication c code using cblas*/**
[B]#include <stdio.h>
#include "cblas.h"
#include <stdlib.h>
#include<string.h>
#include<sys/time.h>[/B]
[B]#ifndef _DEPRECATION_DISABLE   
#define _DEPRECATION_DISABLE   
#if (_MSC_VER >= 1400)         
#pragma warning(disable: 4996) 
#endif 
#endif[/B]
**double A[] = { 1, 2, 3, 4 };**
**double B[] = { 2, 0, 1, 2};**
**double C[] = { 0, 0, 0, 0};**
[B]int main()
{
 int i, j;[/B]
[B] for (i = 0; i<3; ++i) 
 {
  for (j = 0; j<3; ++j) 
   printf("%5.1f", A[i * 3 + j]);
  putchar('\n');
 }[/B]
[B] cblas_dgemm(CblasRowMajor, CblasNoTrans, CblasNoTrans, 3, 3, 3, 1.0, A, 3,
  B, 3, 0.0, C, 3);[/B]
[B] for (i = 0; i<3; ++i)
  printf("%5.1f\n", C[i]);[/B]
[B] return 0;
}

[/B]Thank you very much. Please bear with me I'm new to this Basic Linear Algebra thing.

---

### Post by steeldriver on 2015-07-29
You don't need to compile cblas from source in Ubuntu - it is available as part of the ATLAS base package, which you can install from the Software Center or from the command line using:

```

sudo apt-get install libatlas-base-dev

```

Then you just need to change

```

#include "cblas.h"

```
to
```

#include <cblas.h>

```

in order to find the system version of the header rather than a local version. After that, you should be able to build your code using

```

gcc -o *your_prog* *your_prog*.c -lcblas

```

---

### Post by jsud on 2015-07-30
hi Steeldriver,

Thank you very much I was able to build my code but I had to install some dependencies first.   

_libatlas3-base_ and _libatlas-dev_ are the dependencies for libatlas-base-dev,
_libgfortran3_ is a dependency for libatlas3-base,
_libblas-dev_ is a dependency for libatlas-dev
_and libblas3_ is the dependency for libblas-dev.

---

