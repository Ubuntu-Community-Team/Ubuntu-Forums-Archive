---
title: "Pow() algorithm"
date: 2010-01-17
forum: Programming Talk
---

### Post by s3lcuk on 2010-01-17
hi guys 
i just wanna learn  Pow(x,y) function codes. In fact how can we compute
base 8 and exponent 1/3  result = 2

---

### Post by MadCow108 on 2010-01-17
here's a very detailed page over the square root:
[http://www.azillionmonkeys.com/qed/sqroot.html](http://www.azillionmonkeys.com/qed/sqroot.html)

cubic root calculation should be similar

a little shorter:
[http://en.wikipedia.org/wiki/Cube_root#Numerical_methods](http://en.wikipedia.org/wiki/Cube_root#Numerical_methods)

the pow function will probably use slower but more general methods but on the same line as the sqrt.

very simple method would be:
pow(x,y){
return exp(y*log(x));
}
but this is terribly slow and surly not used in practice :)

---

### Post by Zugzwang on 2010-01-17
> **MadCow108 said:**
> 
very simple method would be:
pow(x,y){
return exp(y*log(x));
}


Actually, AFAIK, this is precisely the method how POW(x,y) is computed for doubles or floats on a x86 machine. As the floating point unit does not have a "pow" function (at least on a Pentium and before) but only "log" and "exp", this is how things are typically done.

---

### Post by jabl on 2010-01-17
If the exponent argument to pow() is an integer, at least g++ can replace the call to the library function pow(double, double) with the faster

```
[FONT=monospace]
[/FONT]TYPE[FONT=monospace]
[/FONT]NAME (TYPE x, int m)
{
  unsigned int n = m < 0 ? -m : m;
  TYPE y = n % 2 ? x : 1;
  while (n >>= 1)
    {
      x = x * x;
      if (n % 2)
        y = y * x;
    }
  return m < 0 ? 1/y : y;
}

```And, if the exponent is a constant integer, it can generate an unrolled version of the above inline.

---

### Post by tom66 on 2010-01-17
pow(x, y) -> exp(y * log(x))

log(x) being the natural logarithm and exp being the exponential function [e(x) = e^x]. To compute exp, use the series 1 + x + (x^2/2!) + (x^3/3!)...; usually, 10-15 terms are suitable to calculate to a reasonable degree; and for log, use the identity log(1 + x) = x + (x^2/2) + (x^3/3) + ... 

I used this to extend php's bc calculator which had no support for decimal exponents.

---

### Post by s3lcuk on 2010-01-19
thank you all guys for answers
i just took an exam programming yesterday 
there will be a couple of question that some well-know functions  (i.w sqrt(),pow()) for programming them.

but unfortunetly there weren't any math function questions...
there were string functions instead of them :D

---

### Post by xander98989 on 2010-02-20
Where can you see the implementation for the math functions? I looked through math.h, mathcalls.h, and mathdef.h but I can't find them or I can't understand what I'm looking at.

---

### Post by akvino on 2010-02-20
> **Zugzwang said:**
> Actually, AFAIK, this is precisely the method how POW(x,y) is computed for doubles or floats on a x86 machine. As the floating point unit does not have a "pow" function (at least on a Pentium and before) but only "log" and "exp", this is how things are typically done.

I learned something new today:

Computation of ab where both a and b are complex
Main article: Exponentiation

Complex exponentiation ab can be defined by converting a to polar coordinates and using the identity (eln(a))b = ab:

---

