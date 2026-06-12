---
title: "Help using GMP in C: How to take non-integer power?"
date: 2009-02-05
forum: Programming Talk
---

### Post by launchcode on 2009-02-05
Hi,

Can anyone tell me how to take a non-integer power using GMP in C?

For example:

y = x ^ 0.2,

where x is a GMP float.

Thanks.

---

### Post by Krupski on 2009-02-05
> **launchcode said:**
> Hi,

Can anyone tell me how to take a non-integer power using GMP in C?

For example:

y = x ^ 0.2,

where x is a GMP float.

Thanks.

Why do you need so much precision? Isn't an ordinary float good enough?

-- Roger

---

### Post by johnl on 2009-02-05
Edit:

Whoops, wrong thread.  Sorry.

---

### Post by PythonPower on 2009-02-05
Well one method I can see involves converting an exponent in the form a^b into a function with exp(). Simply put, a^b = exp(b*ln(a)).

But that relies on the functions exp() and ln() which don't exist. You can implement these yourself in various ways and the computational complexity will be the worst complexity of either function.

Here are some references for starters:
[http://en.wikipedia.org/wiki/Exponential_function#Continued_fractions_for_ex](http://en.wikipedia.org/wiki/Exponential_function#Continued_fractions_for_ex)
[http://en.wikipedia.org/wiki/Logarithm#More_efficient_series](http://en.wikipedia.org/wiki/Logarithm#More_efficient_series)

Hopefully there is a less convoluted way but in absence of that, you have my thoughts. I'll check some other ideas out.

---

### Post by casevh on 2009-02-05
If you need to do it in C, I would use mpfr. It uses GMP for the underlying calculations but provides a much broader set of functions.

You can also use mpmath. It is written in Python but can use GMP for some operations.

casevh

---

### Post by PandaGoat on 2009-02-06
I believe the previous poster hinted to what I will suggest.  Search the following tome for what you seek: [http://gmplib.org/manual/Float-Arithmetic.html#Float-Arithmetic](http://gmplib.org/manual/Float-Arithmetic.html#Float-Arithmetic).  I even turned the pages for you.

---

### Post by launchcode on 2009-02-06
Thanks guys. Much appreciated.

---

