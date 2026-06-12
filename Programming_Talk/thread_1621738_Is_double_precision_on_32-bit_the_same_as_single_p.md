---
title: "Is double precision on 32-bit the same as single precision on 64-bit?"
date: 2010-11-14
forum: Programming Talk
---

### Post by mosquitogang201 on 2010-11-14
I am using gfortran. Is a double precision number compiled on 32-bit Ubuntu the same size as a single precision number compiled on 64-bit Ubuntu?

---

### Post by bouncingwilf on 2010-11-14
It depends on how the compiler defines single and double precision but in general, I would say no. If you want double precision maths, then define the variable as double. In the old days ( maybe still do) we used to specify variable size e.g. Real*4 or Real*8 defining the No. of bytes of Precision.

Bouncingwilf

---

### Post by worksofcraft on 2010-11-14
Although I'm not totally sure about Fortran implementations, in general the floating point and double precision formats are dictated by the floating point processor hardware. evidently that does not depend on whether you use a 64 bit or a 32 OS.
What does change is the size of memory addresses and consequently also the number of bits that it must use as offsets and array indexes. This may affect the size of your integer data type.

---

### Post by Some Penguin on 2010-11-14
[http://en.wikipedia.org/wiki/IEEE_754-2008](http://en.wikipedia.org/wiki/IEEE_754-2008)

---

