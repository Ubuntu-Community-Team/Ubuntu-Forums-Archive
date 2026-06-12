---
title: "mpmath package for python doesn't seem to import properly..."
date: 2008-12-26
forum: Programming Talk
---

### Post by aoanla on 2008-12-26
Hello everyone.

Wanting to do some coding involving non-trivial mathematical functions, I installed the Python mpmath package from the repositories.

However, there's something confusing about how it works:

Trying

from mpmath import *
mp.dps = 15
print besselj(2, 1000)

should return
-0.024777229528606

instead, it returns a complaint about "name 'besselj' is not defined", which suggests that mpmath isn't properly importing all the elements in the namespace (mp.dps works...)
This example is actually in the current documentation:
[http://mpmath.googlecode.com/svn/trunk/doc/build/functions/hypergeometric.html#bessel-functions-besselj-bessely](http://mpmath.googlecode.com/svn/trunk/doc/build/functions/hypergeometric.html#bessel-functions-besselj-bessely)
and I rather assume that it should work for non-svn builds.

Is it just that the version of mpmath in the repos is old enough (0.8 vs the current 0.10) that the available documentation doesn't apply to it? If so, does anyone know what I'm supposed to do to access the relevant parts of the package?

(In a related note, the package that installs matplotlib is also a bit broken - it doesn't appear to contain a valid matplotlibrc, and therefore doesn't do much useful until you provide one yourself...)

---

### Post by nvteighen on 2008-12-26
Hmmm....

```

ugi@UGI:~$ python
Python 2.5.2 (r252:60911, Nov 14 2008, 19:46:32) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mpmath
>>> dir(mpmath)
['__builtins__', '__doc__', '__file__', '__name__', '__path__', 'acos', 'acosh', 'acot', 'acoth', 'acsc', 'acsch', 'agm', 'almosteq', 'apery', 'arange', 'arg', 'asec', 'asech', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'bernoulli', 'bernoulli_range', 'binomial', 'calculus', 'catalan', ...]

```

Nope, no **besselj** function under mpmath 0.8. You may be right and possibly is a new function.

---

### Post by fredrikj on 2008-12-27
Hi, I am the author of the mpmath.

This is indeed a function that isn't available in 0.8. Actually, the besselj function isn't available in the 0.10 release either. You are reading the svn trunk documentation, which as the front page of the mpmath website says, "includes unreleased changes / features". The documentation for the latest release is here:

[http://mpmath.googlecode.com/svn/tags/0.10/doc/build/index.html](http://mpmath.googlecode.com/svn/tags/0.10/doc/build/index.html)

A lot of features, including the Bessel functions, have been added quite recently. If you need the Bessel functions, you can just get the svn trunk of mpmath here:

[http://code.google.com/p/mpmath/source/checkout](http://code.google.com/p/mpmath/source/checkout)

---

