---
title: "Can a double in Java represent every interger a long can store?"
date: 2010-06-30
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-06-30
Can a double in Java represent every integer a long can store?  In other words, when casting from a long to double, is accuracy always preserved?

I read somewhere that it can, but I don't see how since a double must store the decimal pt position and magnitude of exponent while long does not and both are 8 bytes.

---

### Post by Reiger on 2010-06-30
This wiki should clarify that: [http://en.wikipedia.org/wiki/Double_precision_floating-point_format](http://en.wikipedia.org/wiki/Double_precision_floating-point_format)

Basically there is (excluding exceptions such as 0) no 1:1 correspondence between a value x in (unsigned) long notation and an equivalent value y in double notation because double's are defined in terms of approximations of a value, whereas longs are defined in terms of a value (hence the required understanding of the use of significance/thresholds when dealing with floating point computations).

But since both have 8 (bytes) times 8 (bits) of data-points the number of values that they can encode is equal.

---

### Post by MadCow108 on 2010-06-30
no because the (IEEE...) double has only 53 bit in the mantissa which can save integer values, the rest is in the exponent.

So you can only save integers up to 53 bits without losing precision.

consider this (C but Java should gibe same result as it uses the same floating point format):

long long int a = 21412415121234567LL;
double b = a;
printf("%lld %f\n", a ,b);
=
21412415121234567 21412415121234568.000000

not the same

---

