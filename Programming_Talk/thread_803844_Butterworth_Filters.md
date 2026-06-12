---
title: "Butterworth Filters"
date: 2008-05-22
forum: Programming Talk
---

### Post by mj-barton on 2008-05-22
Hi all,

I'm trying to use C++ for determining the coefficients of Butterworth Polynmials for a low pass filter.  I seem to be running into a dead end.  I'm researching for an analytical expressions.  I've dug through wikipedia but what was listed was verbose and confusing.  

Has anyone here done any work with Butterworth Filters?

---

### Post by jpkotta on 2008-05-26
The poles of a Butterworth filter are all on a circle (and they are symmetric about the real axis, because you probably want a real filter); alternatively, the denomiator is related to a cyclotomic polynomial.  The modulus squared of the transfer function (|H(s)|^2) has a cyclotomic polynomial as a denomiator.

The zeros are all at infinity (i.e. it doesn't really have any).

I don't see how the Wikipedia article isn't useful.  It tells you exactly how to calcuate the transfer function.

The way these things are usually built is with pieces with less than 4 poles each.  Deciding how to break it up into the pieces is somewhat dependent on the application.

---

