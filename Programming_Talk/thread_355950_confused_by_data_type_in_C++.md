---
title: "confused by data type in C++"
date: 2007-02-07
forum: Programming Talk
---

### Post by mellibra on 2007-02-07
as we know, C++ has simple data type, like char, wchar_t, int, float, double. So what about long. Is it a data type specifier or a modifier/qualifier. Because I saw some declarations "long long l;", and "long long wchar_t wc;"

How to understand the keyword "long", thank you!

---

### Post by FyreBrand on 2007-02-07
It is a description of an integer.  An int can be long or short.  It can also be signed or unsigned.  Here is a wiki article about long integers in a few languages.  I hope you find it helpful.

[**Wikipedia: Long Integers**]("http://en.wikipedia.org/wiki/Long_integer")

---

### Post by Wybiral on 2007-02-08
"long" and "short" just change the size of the integer. Try using "cout << sizeof(long int);" to see how many bytes it takes up... And "cout << sizeof(short int);"

It just depends how large of a data type you need.

---

### Post by mellibra on 2007-02-08
Thanks, I have checked ISO/IEC 14882, the standard for C++. Actually I confused myself.

In ISO/IEC 14882, char, wchar_t, bool, short, int, long, signed, unsigned, float, double, and voiid are *simple-type-specifier.* So the valid combination of these could specify following types:

void

char
unsigned char
signed char
wchar_t

unsigned / unsigend int
signed / signed int / int
unsigned short int / unsigned short
unsigned long int / unsigned long
signed long int / igned long / long int / long
signed short int / signed short / short int / short

float
double
long double

bool


"long long " is not supported by g++, it is from C99, and supported by gcc.

OK, thanks u 2 guys. ^_^

---

### Post by lnostdal on 2007-02-08
..mentioned here [http://gcc.gnu.org/onlinedocs/gcc/Long-Long.html](http://gcc.gnu.org/onlinedocs/gcc/Long-Long.html)

---

