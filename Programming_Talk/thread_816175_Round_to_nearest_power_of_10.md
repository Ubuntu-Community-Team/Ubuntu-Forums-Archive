---
title: "Round to nearest power of 10"
date: 2008-06-02
forum: Programming Talk
---

### Post by Verminox on 2008-06-02
I'm usually good at Math and algorithms but for some reason my mind is blocked right now and I can't seem to come up with a solution for this quickly.

How do I round x to the nearest power of 10?

For example, 9 => 10, 0.3 => 0.1, 1241 => 1000.

Note that I want to round to the nearest *power* and not *multiple* of 10.

PS: I'm using Java if that's of any relevance (Java sometimes surprises me with it's vast library)


Edit: I know it's got something to do with logs but ...

---

### Post by Bichromat on 2008-06-02
An approximate solution is: 10^round(log10(n))
But it rounds more often towars the superior power because log10(5)>0.5. For example it will round 500 to 1000 even if 500 is closer to 100. So you have to tweak it a bit if that's not what you want.

Edit : here's the tweak I was looking for:
10^round(log10(n) - log10(5.5) + 0.5)

(Because 5.5 is the mean of 1 and 10.)

---

### Post by WW on 2008-06-02
In the following, x must be positive.
```

from math import floor, log

def pow10floor(x):
    return 10**floor(log(x,10))

def pow10round(x):
    return 10**floor(log(x,10)+0.5)

```
pow10floor(x) gives the largest power of 10 that is less than x.

pow10round(x) gives the "nearest" power of 10, but "nearest" is based on first taking a logarithm.  It takes the (base 10) log, rounds that to an integer, then raises 10 to that power. For example, the value of x that is the "midpoint" between 1 and 10 is therefore the value for which log(x,10) = 0.5, which is sqrt(10) (approx. 3.162277).

EDIT:  That code up there is Python, in case you were wondering.  The function floor(y) is the greatest integer less than or equal to y.

---

### Post by Verminox on 2008-06-02
> **Bichromat said:**
> An approximate solution is: 10^round(log10(n))
But it rounds more often towars the superior power because log10(5)>0.5. For example it will round 500 to 1000 even if 500 is closer to 100. So you have to tweak it a bit if that's not what you want.

Edit : here's the tweak I was looking for:
10^round(log10(n) - log10(5.5) + 0.5)

(Because 5.5 is the mean of 1 and 10.)

Actually, we have to consider 5 as the mean of 0 and 10, and not 5.5.

And WW: There is also a need for accounting that log(5) > 0.5....

So it would be something like:
10^round(log(x) - log(5) + 0.5)

However, this notably fails below x<2.....

---

### Post by Lster on 2008-06-02
Do you mean like this?

> 99 	->	100.0
40 	->	10.0
0.001 	->	0.001
1.5 	->	1.0
9 	->	10.0
0.3 	->	0.1
1241 	->	1000.0


EDIT: See Bichromat's first post for a more elegant version of what I posted! :)

---

### Post by Bichromat on 2008-06-02
Lster: what you propose is exactly what my formula does, so it does not seem to be the solution.

---

### Post by Lster on 2008-06-02
Indeed! :) Whoops - I didn't realize that!

---

### Post by WW on 2008-06-02
OK, the pow10round() function I gave earlier seems more "natural" to me, but this should do what you want:
```

from math import floor, log

def pow_round(x):
    return 10**(floor(log(x,10)-log(0.5,10)))

```

Here it is in action:
```

>>> from math import floor, log
>>> 
>>> def pow_round(x):
...     return 10**(floor(log(x,10)-log(0.5,10)))
... 
>>> pow_round(1)
1.0
>>> pow_round(4)
1.0
>>> pow_round(5)
10.0
>>> pow_round(4.99)
1.0
>>> pow_round(9.99)
10.0
>>> pow_round(10.01)
10.0
>>> pow_round(49.99)
10.0
>>> pow_round(50)
10.0
>>> pow_round(50.001)
100.0
>>> pow_round(500.001)
1000.0
>>> pow_round(499.99)
100.0
>>> pow_round(0.3)
0.10000000000000001
>>> pow_round(0.5)
1.0
>>> pow_round(0.99)
1.0
>>> pow_round(0.004)
0.001
>>>

```
The discrepancy at values that are exactly at the midpoint of a range (e.g. 0.5, 5, 50, etc.) is likely the result of floating point imprecision.

---

### Post by Verminox on 2008-06-02
WW: Your code works great :-) 

I just reduced the equation to:

```
10^(floor(log(2*x)))
```

But yes it works just as I wanted it to. Thanks a lot :-)

---

### Post by WW on 2008-06-02
> **Verminox said:**
> 
I just reduced the equation to:

```
10^(floor(log(2*x)))
```

Right, very nice!

---

