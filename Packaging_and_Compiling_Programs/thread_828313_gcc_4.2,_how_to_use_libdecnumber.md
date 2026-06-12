---
title: "gcc 4.2, how to use libdecnumber?"
date: 2008-06-13
forum: Packaging and Compiling Programs
---

### Post by chromaticbum on 2008-06-13
Hello,

I am currently writing an application that requires decimal arithmetic, and I have read that gcc 4.2 supports libdecnumber. I am on ubuntu 8.04 and have gcc 4.2 installed, but I am not sure how to start programming with libdecnum. I try:
#include <decNumber.h>

but the file is not found. Is libdecnumber not included on the ubuntu version of gcc? Or if it is, how do I include the correct headers and link to the library?

Thank you,
Hollin

---

### Post by bruce89 on 2008-06-13
Decimal arithmetic? Surely just the normal C adding and multiplying and so on. That doesn't need any headers to be included.

---

### Post by Alysander on 2008-06-14
Hi,

I also would like to use libdecnumber. The official Intel page ([http://www2.hursley.ibm.com/decimal/](http://www2.hursley.ibm.com/decimal/)) indicates it is in GCC 4.2.
However, it appears from this page ([http://archives.devshed.com/forums/development-94/new-decnumber-sources-need-gpl-exception-for-use-in-libgcc-1875888.html](http://archives.devshed.com/forums/development-94/new-decnumber-sources-need-gpl-exception-for-use-in-libgcc-1875888.html)) that it is not enabled in 4.2 and mainline unless configured to use it at compile time.

GCC has a little documentation:
[http://gcc.gnu.org/onlinedocs/gcc/Decimal-Float.html#Decimal-Float](http://gcc.gnu.org/onlinedocs/gcc/Decimal-Float.html#Decimal-Float)

If you use the snapshot version of gcc (apt-get gcc-snapshot) it has some support for the proposed base 10 extension to the C language.
[http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1154.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1154.pdf)
The binary is installed in /usr/lib/gcc-snapshot/bin/gcc

It appears that the printf format specifiers for base 10 (%H, %DD and %DL) are not working yet.  Anyway here is an example program that compiles with the snapshot version of gcc to compare floats and _Decimal32 precision:

```

#include <stdio.h>

int main()
{
  _Decimal32 number1 = 0.3df;
  float number2 = 0.3;
  float number3 = 1.4;
  _Decimal32 number4 = 1.4df;
  int i;
  
  for(i = 0; i < 11; i++) {
    number1 += 0.1df;
    number2 += 0.1; 
  }
  
  printf("Iterated Decimal converted to float is %.20f\n", (float)number1);
  printf("Iterated float is %.20f\n", number2);
  printf("Initialized float is %.20f\n", number3);
  printf("Initialized Decimal converted to float is %.20f\n", (float)number4);  
  return 0;
}
```

The output on my machine is:

Iterated Decimal converted to float is 1.39999999999999991118
Iterated float is 1.40000021457672119141
Initialized float is 1.39999997615814208984
Initialized Decimal converted to float is 1.39999999999999991118

So it looks like _Decimal32 is preserving the data correctly and only
losing precision in the printf and not during additions like the float is.

Hope this helps :)
-Alysander

---

### Post by chromaticbum on 2008-06-15
Alysander,

Thank you for the response. I will try to get this working when I go into work tomorrow. Too bad the printf formatting doesn't work, but maybe it will get fixed soon enough.

---

### Post by chromaticbum on 2008-06-18
So I have implemented the part of my program using _Decimal32 that needed it. It works fine, but it is too bad that GCC-snapshot does not show great support for this type (ie: no math functions and no printf formatting). Anyways, I was able to implement the math functions I needed in software until I get the optimized implementations with another release of gcc.

Thank you again Alysander

---

