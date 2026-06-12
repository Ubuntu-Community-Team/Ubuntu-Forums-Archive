---
title: "Python optimising"
date: 2009-10-15
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-10-15
Hi All

I was wondering if there is any difference in execution time when using things like unary if and and compressing those for loops into the one line sort, (I forget what they are called).

What is the difference if any in execution time?

MIke

---

### Post by unutbu on 2009-10-15
Here is some fairly general-purpose code which has been setup to compare a (for-loop with an if-statement) versus a list comprehension:

[PHP]#!/usr/bin/env python
import time

def print_timing(func):
    def wrapper(*arg):
        t1 = time.time()
        res = func(*arg)
        t2 = time.time()
        print '%s took %0.3fms.' % (func.func_name, (t2-t1)*1000.)
        return res
    return wrapper

N=100000

@print_timing
def f1():
    result=[]
    for i in range(N):
        if i%7==0:
            result.append(i)
    return result

@print_timing
def f2():
    result=[i for i in range(N) if i%7==0]
    return result

f1()
f2()[/PHP]

Output:```

% test.py
f1 took 38.152ms.
f2 took 24.463ms.
```

This shows that list comprehensions might be faster than for-loops with if-statements.(*)

I'm not sure if this answers your question, but if not, you can stick your own code in f1 and f2 to compare various bits of code.

(*)Upon running the above code a couple of times, I find results are not always significantly different, and in a few runs, the for-loop was faster than the list comprehension.

---

### Post by CptPicard on 2009-10-15
I don't know what the python runtime actually does, but an interesting point about the list comprehension vs. a loop is that the former is declarative, that is, it defines directly what the end result list *is*, while for the loop is potentially harder to analyze and at worst would need to be actually run to know what it does.

It's just a gut feeling that if I were authoring a language, optimizing a list comprehension might be easier...

---

### Post by Can+~ on 2009-10-15
> **unutbu said:**
> Here is some fairly general-purpose code which has been setup to compare a (for-loop with an if-statement) versus a list comprehension:

Take a look at:
[http://docs.python.org/library/timeit.html](http://docs.python.org/library/timeit.html)

---

### Post by unutbu on 2009-10-15
Can+~, I used to use timeit, but find the syntax a little cumbersome:

[PHP]import timeit
num=100
N=10000

def f1():
    result=[]    
    for i in xrange(N):
        if i%7==0:
            result.append(i)
    return result

def f2():
    result=[i for i in xrange(N) if i%7==0]
    return result

funcname_list=[key for key in locals().keys() if callable(locals()[key])]
for funcname in funcname_list:
    initial='''
from __main__ import %s
'''%funcname
    timer=timeit.Timer('%s()'%funcname,initial)
    dt=timer.timeit(num)
    print "Time using %s: %0.3f secs"%(funcname,dt)
[/PHP]
The @print_timing decorator seems to me a bit more straight-forward than setting up initial and funcname strings. 

Do you know of any reason why using the timeit module is superior?

---

### Post by Can+~ on 2009-10-15
Mostly because it does multiple repetitions on it's own, but aside of that, I agree with you, the syntax for it is very cumbersome.

---

### Post by Mickeysofine1972 on 2009-10-15
So then,

No guessing whats the best speed wise :D

Thanks for the info !

Mike

---

### Post by wmcbrine on 2009-10-15
Forget speed... list comprehension is just cooler. :)

---

### Post by Mickeysofine1972 on 2009-10-15
> **wmcbrine said:**
> Forget speed... list comprehension is just cooler. :)

Well cool it may be. But i prefer just to have the right tool for the job.

Which it appears to be in my case :D

Mike

---

