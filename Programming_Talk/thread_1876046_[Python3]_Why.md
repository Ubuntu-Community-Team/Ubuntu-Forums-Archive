---
title: "[Python3] Why?"
date: 2011-11-05
forum: Programming Talk
---

### Post by donsy on 2011-11-05
Python 2.x correctly returns binomial coefficients and permutations as integers or longs. Why was this changed in py3?
```
Python 3.2.2 (default, Sep  5 2011, 22:09:30) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from math import factorial
>>> factorial(6)/(factorial(3)*factorial(3))
20.0
>>> factorial(6)
720
>>> factorial(6)/factorial(3)
120.0
>>> 

```I know I can always wrap the expressions in int(). But that shouldn't be necessary because binomial coefficients and permutations are always int's and it makes about as much sense as```
>>> int(float(42))
42
>>>
```

---

### Post by Bachstelze on 2011-11-05
*sigh*

Integer division in Python 3 is done with //. You could have just asked instead of going on a rant about how it doesn't make sense, because if anything, how Python 2 does it makes even less.

---

### Post by donsy on 2011-11-05
I stand corrected.

---

