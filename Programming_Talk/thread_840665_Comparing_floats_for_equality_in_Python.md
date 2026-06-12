---
title: "Comparing floats for equality in Python"
date: 2008-06-25
forum: Programming Talk
---

### Post by xn__ on 2008-06-25
Hello all,
I'm new to the forums here, and apologies if this has been covered before, but... How bad is it *really* to test floating point variables for equality in Python? Will I always get away with this sort of thing:

a=0.5
b=0.5
if a==b:
    print "a equals b"

or, for example:

if a-b==0.:
    print "a equals b"

I'm guessing I don't want to do too many (different?) operations on a and b before testing them for equality, but will Python let me do the above? Is there a more Pythonic way of doing this that is reliable to some pre-specified tolerance?

Thanks,
Christian

---

### Post by LaRoza on 2008-06-25
To compare floats (in any languages) you use < and >.

---

### Post by xn__ on 2008-06-25
> **LaRoza said:**
> To compare floats (in any languages) you use < and >.

Well, apart from Fortran (.lt. and .gt.). But perhaps I didn't express myself clearly: I meant to test to see if two floats are equal to one another. In Python, the above code works in the same way as it would with integers, and my question was about whether this behaviour is always guaranteed to work.
How do other people do this?

---

### Post by unutbu on 2008-06-25
```
#!/usr/bin/env python

def feq(a,b):
    if abs(a-b)<0.00000001:
        return 1
    else:
        return 0

a=0.33333333
b=1.0/3
print "a="+"%s"%a+"\tb="+"%s"%b
if feq(a,b):
    print "a equals b"
else:
    print "a does not equal b"

```

Change 0.00000001 to taste (depending on the application), or perhaps use the largest value epsilon for which a equals a+epsilon on your system.

```
#!/usr/bin/env python
def feq(a,b):
    if abs(a-b)<0.00000001:
        return 1
    else:
        return 0

a=0
epsilon=1.0
b=a+epsilon
done=0
while not done:
    if feq(a,b):
        print "epsilon=%s"%epsilon
        done=1
    else:
        epsilon=epsilon/2
        b=a+epsilon
```

The result on my system is
```
% test.py
epsilon=7.45058059692e-09
```

So this epsilon appears to be the largest float value that is indistinguishable from zero on my system.

---

### Post by xn__ on 2008-06-25
Thanks: that's certainly the way I'd do it if values like 1./3. or 1./10. could come up. But my floats are all quantum numbers which are integer or half-integer, and I don't do anything too exotic to them (maybe take one from another or add them or the like). Since half-integers can be represented precisely, does that mean that 0.5 is always == to 1.5 - 1. and so on? It seems to be working, but I don't want any nasty surprises down the road.

---

### Post by Can+~ on 2008-06-25
> **xn__ said:**
> Thanks: that's certainly the way I'd do it if values like 1./3. or 1./10. could come up. But my floats are all quantum numbers which are integer or half-integer, and I don't do anything too exotic to them (maybe take one from another or add them or the like). Since half-integers can be represented precisely, does that mean that 0.5 is always == to 1.5 - 1. and so on? It seems to be working, but I don't want any nasty surprises down the road.

Read this:
[http://pyfaq.infogami.com/why-are-floating-point-calculations-so-inaccurate](http://pyfaq.infogami.com/why-are-floating-point-calculations-so-inaccurate)

The thing is that floating point calculations have imprecisions, always. Doing "1.0 - 0.1" in the interactive shell will produce a little inaccuracy. That's why is recommended to work with < and >.

Check the Decimal module:
[http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html)

---

### Post by xn__ on 2008-06-26
Thanks guys. I'll need to call my feq function in lots of classes, defined in lots of different files. Is there a better way of giving these classes access to it than shoving it in a globals.py file and having a from globals import * line at the start of each file?
xn

---

### Post by blis102 on 2011-02-14
Sorry for digging up such an old thread, but in case people stumble across this, it could prove useful.


Try watching this Computer Science lecture on Floats by an MIT professor:

[http://www.youtube.com/watch?v=Pfo7r6bjSqI](http://www.youtube.com/watch?v=Pfo7r6bjSqI)

It will explain why floats behave this way in computers and how to work with them. It actually deals with Python too, which is nice.

I'd recommend watching the whole lecture series actually if you don't have a CS background.

Cheers

---

### Post by Poirot on 2012-11-22
```
def float_eq(a, b, epsilon=0.00000001):
    return abs(a - b) < epsilon

a = 0
epsilon = 1.0
while not float_eq(a, epsilon):
    epsilon /= 2
```

---

### Post by StephenF on 2012-11-23
You might find the fractions module useful.
```

>>> from fractions import Fraction
>>> Fraction(1.1) - Fraction(11, 10)
Fraction(1, 11258999068426240)

```

---

