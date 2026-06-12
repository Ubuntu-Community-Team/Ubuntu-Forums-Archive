---
title: "[Python] why does this subtraction equal zero sometimes, but not always?"
date: 2010-04-15
forum: Programming Talk
---

### Post by skullmunky on 2010-04-15
I've seen some explanations of floating-point inaccuracy with complicated arithmetic, where the result is close to but not really zero.  But I'm wondering why this doesn't work either:

```

a=1.0
while a>0:
  a=a-0.1
  print a

```

I get:
```

0.9
0.8
0.7
0.6
0.5
0.4
0.3
0.2
0.1
1.38777878078e-16
-0.1

```

but this gives me zero:
```

b=0.1
b=b-0.1

```

shouldn't that be the same thing ... ?

---

### Post by MadCow108 on 2010-04-15
this has to do with the floating point representation on computers

a IEEE... floating point is not capable of representing all fractions exactly, thus you get rounding errors.
0.1 may be represented as 0.1000000001.
In the second the rounding errors are identical so you get e.g. 0.1000000001 - 0.1000000001 = 0
wheras in the first case you have e.g:
10.0 - 0.1000000001 = 0.90000000
0.90000000 - 0.1000000001 = 0.88999998
so you don't arrive at zero

the python decimal module is capable of representing fractions exactly, so use that is it is a problem

---

### Post by Tony Flury on 2010-04-15
three words - Floation point errors : 

All numbers are generally represented as binary fractions - a sum of 1/2, 1/4, 1/8, 1/16, 1/32 etc (similar to the way integers are represented).

your series of 0.9, 0.8, 0.7 can't be represented accurately this way, and so the language makes an approximation - so although 1.0 is accurate - the 0.1 is approximate there fore the 0.9 result is actually internally an approximation. Next iteration the approximated 0.1 is subtracted from the approximated 0.9 - leading to an approximated 0.8 - and so errors creep in - and when your programm outputs 0.1, it is actually holding a value closer to 0.10000000000000001 (or something like that), which may not be the same approximation that the compiler would create for 0.1 when it sees it as a literal.

The reason that your second fragment returns 0 "correctly" is that the compiler is creating the same value for 0.1 on both lines - and so the subtraction is equal to zero.

See [http://en.wikipedia.org/wiki/Floating_point_error#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point_error#Accuracy_problems) - that might help

---

