---
title: "Question regarding static library"
date: 2009-11-18
forum: Programming Talk
---

### Post by hellishfire on 2009-11-18
Hello, recently I began to try compiling programs without an IDE, and gcc is the tool I use(gcc version 4.3.3 in ubuntu 9.04).

The sample program is a simple one, written in C.

#include <stdio.h>
#include <math.h>
int main(){
  double a=2.0;
  double x=sqrt(a);
  printf("result=%f\n",x);
  return 0;
}

I took four different approaches to compile this code.

gcc sqrt.c -lm -o sqrt_default
gcc sqrt.c /usr/lib/libm.so -o sqrt_dynamic
gcc sqrt.c -static -lm -o sqrt_static_1
gcc sqrt.c /usr/lib/libm.a -o sqrt_static_2

All compilations were successful, and the results were as follows:
-rwxr-xr-x 1 oracle oracle   9186 2009-11-18 13:16 sqrt_default
-rwxr-xr-x 1 oracle oracle   9186 2009-11-18 13:16 sqrt_dynamic
-rwxr-xr-x 1 oracle oracle 597277 2009-11-18 13:16 sqrt_static_1
-rwxr-xr-x 1 oracle oracle  22176 2009-11-18 13:16 sqrt_static_2

The first two compilations shared the same file size(9186), which is to be expected given the fact that gcc uses dynamic library as default.

However, the latter two confused me. I assumed that the latter two both used static library, yet their file sizes were quite different(597277 vs 22176).
Can someone tell me why? Aren't (-static -lm) and (/usr/lib/libm.a) the same thing?

Thanks in advance!

---

### Post by Arndt on 2009-11-18
> **hellishfire said:**
> Hello, recently I began to try compiling programs without an IDE, and gcc is the tool I use(gcc version 4.3.3 in ubuntu 9.04).

The sample program is a simple one, written in C.

#include <stdio.h>
#include <math.h>
int main(){
  double a=2.0;
  double x=sqrt(a);
  printf("result=%f\n",x);
  return 0;
}

I took four different approaches to compile this code.

gcc sqrt.c -lm -o sqrt_default
gcc sqrt.c /usr/lib/libm.so -o sqrt_dynamic
gcc sqrt.c -static -lm -o sqrt_static_1
gcc sqrt.c /usr/lib/libm.a -o sqrt_static_2

All compilations were successful, and the results were as follows:
-rwxr-xr-x 1 oracle oracle   9186 2009-11-18 13:16 sqrt_default
-rwxr-xr-x 1 oracle oracle   9186 2009-11-18 13:16 sqrt_dynamic
-rwxr-xr-x 1 oracle oracle 597277 2009-11-18 13:16 sqrt_static_1
-rwxr-xr-x 1 oracle oracle  22176 2009-11-18 13:16 sqrt_static_2

The first two compilations shared the same file size(9186), which is to be expected given the fact that gcc uses dynamic library as default.

However, the latter two confused me. I assumed that the latter two both used static library, yet their file sizes were quite different(597277 vs 22176).
Can someone tell me why? Aren't (-static -lm) and (/usr/lib/libm.a) the same thing?

Thanks in advance!

They may be the same as regards the handling of libm.a, but you haven't taken libc.a into account. That is the largest part of sqrt_static_1.

---

### Post by hellishfire on 2009-11-18
Ah, I get it now. Thanks!

---

