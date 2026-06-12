---
title: "Taking large floating input"
date: 2009-03-01
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-01
When taking large floating input(eg:2.99999999999999999999). Python converts it to 3.0

How do i avoid such conversion, so that i get 2.99999999... as the value stored.

---

### Post by WW on 2009-03-01
[Floating point numbers in python](http://docs.python.org/tutorial/floatingpoint.html) are finite precision.  If you really need arbitrary precision, libraries such as [mpmath](http://code.google.com/p/mpmath/) are available.

---

### Post by CptPicard on 2009-03-01
Look at the decimal module (class Decimal) for fixed point.

---

### Post by rharriso on 2009-03-01
There are string based libraries in C++ and java for handling arbitrarily large numbers, you should see if they exist for python.

---

### Post by kavon89 on 2009-03-02
> **rharriso said:**
> There are string based libraries in C++ and java for handling arbitrarily large numbers, you should see if they exist for python.

BigDecimal?

---

### Post by tneva82 on 2009-03-02
> **kavon89 said:**
> BigDecimal?

Sounds what I used when I needed really BIG numbers for cryptograph program.

---

