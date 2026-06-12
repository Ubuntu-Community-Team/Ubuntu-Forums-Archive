---
title: "math module for python"
date: 2008-11-02
forum: Programming Talk
---

### Post by karloo on 2008-11-02
I started solving problems from project euler a month ago. However, I noticed that algorithms written in Pythom, run much slower than those in C++, for example. That's way I am looking now for a good math module. I installed gmpy, but I am still not satisfied since it contains only a few math functions. Anyone could recommend me a good math module?

---

### Post by WW on 2008-11-02
"Math" is a very broad subject area.  Are there specific functions you are looking for?

You mention Project Euler, so these might not be what you want,  but take a look at [Numpy](http://numpy.scipy.org/) and [Scipy](http://www.scipy.org/).

---

### Post by karloo on 2008-11-02
You're right: math is a broad subject. For example, functions like those available in PARI/GP would interest me most (therefore functions related to number theory). I have numpy installed (I only used it a couple of times for some Soar applications though) and I'll take a look at Scipy. Any other suggestions?

---

### Post by casevh on 2008-11-02
You may want to check out [mpmath]("http://code.google.com/p/mpmath/"), [sympy]("http://code.google.com/p/sympy/"), or [sage]("http://www.sagemath.org/").

casevh

---

### Post by karloo on 2008-11-03
Thanks casevk. Hope now it will be easier to satisfy the one minute rule:)

---

### Post by Paul Miller on 2008-11-03
> **karloo said:**
> Thanks casevk. Hope now it will be easier to satisfy the one minute rule:)

I think you'll find most of the time that making numerical calculations faster won't pay dividends as big as using better algorithms (i.e. thinking a little bit more).

---

### Post by DevilzDriv3r on 2008-11-03
like paul miller said, the main idea is to find the most efficient algorithm, that will take at least one-minute to find the answer. by the way, which challenge are you trying to solve?

---

### Post by karloo on 2008-11-04
I agree that finding a good algorithm is the best way to solve those problems. However, as I mentioned in my first post, such algorithms take much more time in Python usually. My prime sieve, for example, can generate quite quickly all primes up to 10**7, but takes forever for 10**8. On the other hand, the is_prime function from gmpy (written in C i think...) does the job in just a few seconds. 
@DevilzDriv3r: After finishing the first 50 pbs (well, almost...) I started doing problems randomly. As far as I remember the last one I tried was 191. Not yet done with it but I'm close :) Hope I'll have 100 pbs done by the end of the year:)


PS: I installed sage on Ubuntu. Anyone knows if I can use it with IDLE? I am kind of confused when it comes to use it.

---

