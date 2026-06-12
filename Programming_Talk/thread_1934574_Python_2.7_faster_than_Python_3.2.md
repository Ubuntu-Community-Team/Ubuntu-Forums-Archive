---
title: "Python 2.7 faster than Python 3.2"
date: 2012-03-02
forum: Programming Talk
---

### Post by ntanitime on 2012-03-02
Hi,
I run this script first in Python IDE 2.7 and after in IDE 3.2.
```
import time
import sys
xxx=range(10000)

def timer(func, *pargs, **kargs):
    start=time.clock()
    for i in xxx:
        res = func(*pargs, **kargs)
    ela = time.clock() -start
    return (ela,res)

def forLoop():
    res = []
    for x in xxx:
        res.append(abs(x))
    return res

def listComp():
    return [abs(x) for x in xxx]



def mapCall():
    return list(map(abs, xxx))

def genExpr():
    return list(abs(x) for x in xxx)

def genFun():
    def gen():
        for x in xxx:
            yield abs(x)
    return list(gen())

print(sys.version)
for test in (forLoop, listComp, mapCall, genExpr, genFun):
    ela, resu = timer(test)
    print ('-'*33)
    print ('%-9s: %.5f => [%s...%s]' % (test.__name__, ela, resu[0], resu[-1]))
```Python 2.7:

```
>>> 
2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1]
---------------------------------
forLoop  : 13.03000 => [0...9999]
---------------------------------
listComp : 6.99000 => [0...9999]
---------------------------------
mapCall  : 5.42000 => [0...9999]
---------------------------------
genExpr  : 9.70000 => [0...9999]
---------------------------------
genFun   : 9.74000 => [0...9999]
>>> 
2.7.2+ (default, Oct  4 2011, 20:06:09) 
[GCC 4.6.1]
---------------------------------
forLoop  : 12.42000 => [0...9999]
---------------------------------
listComp : 6.99000 => [0...9999]
---------------------------------
mapCall  : 5.80000 => [0...9999]
---------------------------------
genExpr  : 9.72000 => [0...9999]
---------------------------------
genFun   : 9.72000 => [0...9999]
```Python 3.2:

```
>>> 
3.2.2 (default, Sep  5 2011, 21:17:14) 
[GCC 4.6.1]
---------------------------------
forLoop  : 13.89000 => [0...9999]
---------------------------------
listComp : 8.61000 => [0...9999]
---------------------------------
mapCall  : 6.29000 => [0...9999]
---------------------------------
genExpr  : 11.42000 => [0...9999]
---------------------------------
genFun   : 11.27000 => [0...9999]
>>> 
3.2.2 (default, Sep  5 2011, 21:17:14) 
[GCC 4.6.1]
---------------------------------
forLoop  : 14.18000 => [0...9999]
---------------------------------
listComp : 8.58000 => [0...9999]
---------------------------------
mapCall  : 6.47000 => [0...9999]
---------------------------------
genExpr  : 11.61000 => [0...9999]
---------------------------------
genFun   : 11.44000 => [0...9999]
```Why Python 2.7 is faster than 3.2 ???
is it ok ?

---

### Post by MadCow108 on 2012-03-02
that is to be expected.
python3 was always slower than python2, there are many changes that make programming simpler but also make it slower (no special casing for small integers, unicode, generators everywhere).
the memory usage also increases a lot due to unicode (though it will be reduced a bit again with the flexible string representation in 3.3, again at the cost of a little more performance)

It may improve in future but I would not count on anything really significant, cpython goal is not to be the fastest interpreter.
Other interpreters like pypy, ironpyhon or jython may be faster (but to my knowledge none of these supports py3 yet)

---

### Post by ntanitime on 2012-03-03
Thanks you :)
I hope they improve 3.2 in the future because speed is one of the most important value!

---

### Post by ofnuts on 2012-03-03
> **ntanitime said:**
> Thanks you :)
I hope they improve 3.2 in the future because speed is one of the most important value!
Not really... just wait for next year's computer.

---

### Post by ntanitime on 2012-03-07
So for you speed isn't important value ?

---

### Post by simeon87 on 2012-03-07
It is, but we're not using Python for speed.

---

### Post by ofnuts on 2012-03-07
> **ntanitime said:**
> So for you speed isn't important value ?It is, but 10% or 20% faster isn't really significant, it's the difference between an el-cheapo computer and something still reasonable, or between my current machine and my future machine. If I wanted real speed for something I would use a fully compiled language (if my algorithms can't be improved).

This said, python is quite fast...

---

### Post by cgroza on 2012-03-07
And I think you can still write the speed critical code in C and use it in Python.

---

### Post by llanitedave on 2012-03-08
I can't find it right now, but a few months back I did a comparison and Python 3.2 was faster on floating point operations within a loop.

So your benchmarks depend in part on the type of operation being performed.

BTW, I also found that the speed of javascript has increased tremendously over the past few years, and it's pretty comparable to python.

---

### Post by ntanitime on 2012-03-08
> **cgroza said:**
> And I think you can still write the speed critical code in C and use it in Python.

yes this can increase drastically your speed**:D**

---

