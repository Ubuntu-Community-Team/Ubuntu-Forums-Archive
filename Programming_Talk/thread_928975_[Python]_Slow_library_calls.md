---
title: "[Python] Slow library calls?"
date: 2008-09-24
forum: Programming Talk
---

### Post by Erdaron on 2008-09-24
As a matter of tinkering with programming, I tried the following code in Python:
[PHP]from numpy import mean
from time import time
from random import uniform

def pymean(a):
    s = 0
    for n in a:
        s = s + n
    return s / len(a)

a = []

for j in range(1e6):
    a.append([uniform(0,10), uniform(0,10), uniform(0,10),uniform(0,10),uniform(0,10)])

t0 = time()
for b in a:
    c = pymean(b)
print str(time() - t0)

t0 = time()
for b in a:
    c = mean(b)
print str(time() - t0)[/PHP]

Numpy is a library that uses C bindings to speed up numerical calculations, so it should be faster, right? In my test, using pymean() cranked through this set in 1.5 seconds, while numpy.mean() took 50 seconds. I ran the test several times to make sure it wasn't some timing fluke, and this result was quite consistent. I assume the difference must be due to calling on an external library a million times.

A data analysis script I wrote for work calls on numpy about half a million to a million times in processing a single experiment, and it is significantly slower than a commercial program doing the same algorithm.

Is there a way to speed up such calls?

Thank you for enlightening my ignorance!

---

### Post by olejorgen on 2008-09-29
Speculation follows:
numpy.mean causes a dict query.
Setting npy_mean = numpy.mean and use npy_mean in place of numpy.mean should help

EDIT: hm.. that's probably not it, condsidering the huge difference. Ups, didn't even read you code right, sorry :)

---

### Post by y-lee on 2008-09-29
I had the same problem using numpy with some code I wrote a couple of months ago. Namely using numpy slowed my code done significantly :confused:

mistaken, sorry

---

### Post by DaymItzJack on 2008-09-29
I can't explain the numpy calls but I can say that using sum() **is** faster than:

```
    for n in a:
        s = s + n 
```

---

### Post by meanburrito920 on 2008-09-29
As I just recently found out from Wybiral on a separate thread, the reason for this problem is the fact that accessing a function through numpy causes a lookup on the global scope, but first python looks through local, and then slowly progresses to global. Every time. What you want to do is define numpy.mean as _mean within the code body itself so that it is only doing a local function lookup. That should make all the difference.

so try this:

```

_mean = mean
t0 = time()
for b in a:
    c = _mean(b)
print str(time() - t0)  

```

---

### Post by meanburrito920 on 2008-09-29
Uh oh... I tried this out and it didn't help, which really suprised me. Maybe numpy has a messed up mean function?


Edit: GAHHH! I can't believe I missed the entire question. Well, it wouldnt be the first time...

---

### Post by olejorgen on 2008-09-29
No, you wasn't :)
```

         30001 function calls in 1.185 CPU seconds

   Ordered by: internal time, call count

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
    10000    0.440    0.000    0.440    0.000 numeric.py:129(asarray)
    10000    0.415    0.000    0.855    0.000 fromnumeric.py:32(_wrapit)
    10000    0.227    0.000    1.082    0.000 fromnumeric.py:1752(mean)
        1    0.103    0.103    1.185    1.185 test.py:27(numpy)
        0    0.000             0.000          profile:0(profiler)
---
a.append(asarray([uniform(0,10), uniform(0,10), uniform(0,10),uniform(0,10),uniform(0,10)]))
:
         10001 function calls in 0.301 CPU seconds

   Ordered by: internal time, call count

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
    10000    0.242    0.000    0.242    0.000 fromnumeric.py:1752(mean)
        1    0.059    0.059    0.301    0.301 test.py:29(numpy)
        0    0.000             0.000          profile:0(profiler)
---
e4 times:
py: 0.175576925278
numpy: 0.218255996704
---
e6 times:
py: 17.5256340504
numpy: 20.3674850464

```

The built in is still faster (I used sum(b) / len(b) though) but that might be expected since the arrays is pretty short. Although the sum might be fastest in this case anyway. I bet that is done in C.

PS: profiling is a great tool [http://docs.python.org/lib/hotshot-example.html](http://docs.python.org/lib/hotshot-example.html)

---

### Post by olejorgen on 2008-09-29
Nope, with about 10 times as many items in each array. e5 times:
```

py 63.0911090374
numpy: 2.47154903412

```

---

### Post by Erdaron on 2008-09-30
Wow, I thought this thread simply died!

> **olejorgen said:**
> Nope, with about 10 times as many items in each array. e5 times:
```

py 63.0911090374
numpy: 2.47154903412

```

I was wondering if that will be the case. Which reinforces my suspicion that a library call is slow, while the library itself may be fast. So if you're dealing with a very long vector, numpy maybe the win.

It didn't seem to me that renaming a function locally would speed it up, since function's instructions are still stored in another library. Giving it a local name simply points there (again). At least this makes sense to me.

And yes, I'm sure the sum() is faster than summing it all "by hand." I'm still new - glad to have learned something :).

---

### Post by olejorgen on 2008-09-30
> It didn't seem to me that renaming a function locally would speed it up, since function's instructions are still stored in another library. Giving it a local name simply points there (again). At least this makes sense to me.
Yes, the dominating cost will be the function call, but when python sees this: pynum.mean it will have to lookup what pynum is, and then lookup what mean is. This is due to python's extremly dynamic nature. When you assign mean = pynum.mean you get rid of one lookup.

Note that this was not a problem in you case (I think) since you used from pynum import mean.

Disclaimer: I guess some optimizations is done in some situations (?) but I think this should be fairly accurate.

> I was wondering if that will be the case. Which reinforces my suspicion that a library call is slow, while the library itself may be fast. So if you're dealing with a very long vector, numpy maybe the win.
Yes it seems like they are a bit slower. I think you might have missed my, or rather y-lee's, point though: It's the conversion from list to pynum.array that was really expensive.

(WRONG) I don't think the list need to be very long before pynum wins if you use pynum.array from the start. Of course, this might slow down other parts of your program.

---

### Post by olejorgen on 2008-09-30
Sorry, I've been a little sloppy:
1. Forgot to set cpu governour to max
2. I fed sum pynum.arrays. It likes lists better.
3. The tests should also be run independent of eachother

```

from numpy import mean 
from numpy import asarray 
from random import uniform
from time import time

pynummean = mean # probably no point

pyargs = [] 
pynumargs = [] 

def pymean(values):
	return sum(values) / len(values)

def py(args):
	for b in args: 
		c = pymean(b)
def inlinepy(args):
	for b in args: 
		c = sum(b) / len(b) 
def numpy(args):
	for b in args: 
		c = pynummean(b) 

import sys

M = 50
N = int(1e5)
def listargs():
	return [[uniform(0,10) for x in range(M)] for y in range(N)]
def arrayargs():
	return [asarray([uniform(0,10) for x in range(M)]) for y in range(N)]
def test(fun, args):
	t0 = time() 
	fun(args)
	t1 = time()
	print fun.__name__, str(t1-t0)


if sys.argv[1] == "py":
	test(py, listargs())
elif sys.argv[1] == "pynum":
	test(numpy, arrayargs())
else:
	test(inlinepy, listargs())

```
Results:
```

# N = e5
# M = 50
$ python test.py py
py: 1.16485118866
$ python test.py pynum
numpy: 2.21901512146
$ python test.py inlinepy
inlinepy: 1.09585213661
# N = e4
# M = 500
$ python test.py py
py: 0.875946998596
$ python test.py pynum
numpy: 0.280221939087
$ python test.py inlinepy
inlinepy: 0.876913070679

```

I guess a lesson is learned here :)

> It's the conversion from list to pynum.array that was really expensive. still stands though

---

### Post by WW on 2008-10-08
You can do a lot better with numpy.  When you find yourself writing a loop for a simple calculation like this, stop and look more closely at what you are doing.  There is probably a more efficient way to do it with numpy.

Here are two versions of your calculation. The first version puts the data in an NxM numpy array, and uses a single call to the mean function with the argument axis=1 to compute the averages of all the rows.  The second version is a pared down version of your fastest case when M=50 and N=1e5:

```

# meantest.py

from numpy import mean
from numpy.random import uniform
from time import time


M = 50
N = int(1e5)

a = uniform(size=(N,M))

t0 = time()
c = a.mean(axis=1)
t1 = time()
print str(t1-t0)

```
```

# meantest2.py

from time import time
from random import uniform

M = 50
N = int(1e5)

a = [[uniform(0,10) for x in range(M)] for y in range(N)]

t0 = time() 
for row in a: 
    c = sum(row) / len(row) 
t1 = time()
print str(t1-t0)

```
Results:
```

$ python meantest.py 
0.198862075806
$ python meantest.py 
0.214025020599
$ python meantest2.py 
2.23573708534
$ python meantest2.py 
2.2262699604
$ 

```
The numpy version is better than 10 times faster.

---

