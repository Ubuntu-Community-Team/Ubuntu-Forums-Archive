---
title: "Python: x**y vs pow(x,y)"
date: 2010-04-01
forum: Programming Talk
---

### Post by lavinog on 2010-04-01
I notice a lot of people use math.pow instead of the ** operator.
I wrote a benchmark test to see if there was a difference And I don't quite understand the results:
```

Testing with int values
pow(x,y)   :  0.691752910614
x ** y     :  1.92788410187
x ** 0.5   :  0.404187917709
sqrt(x)    :  0.352621078491
Testing with float values
pow(x,y)   :  0.677602052689
x ** y     :  0.346560001373
x ** 0.5   :  0.366789102554
sqrt(x)    :  0.344245910645

```

So x**y is 3x slower than pow(x,y) when x and y are ints, but x**y is 2x faster when x and y are both floats.

Why should there be such a drastic difference?
I am using Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 

Here is the code I used to test it:
[php]
#!/usr/bin/env python

import math
import time
import random
def mathpowtest(values):
    '''pow(x,y)'''
    for x, y in values:
        v = math.pow(x,y)

def builtinpowtest(values):
    '''x ** y'''
    for x, y in values:
        v = x ** y

def mathsqrttest(values):
    '''sqrt(x)'''
    for x, y in values:
        v = math.sqrt(x)

def builtinsqrttest(values):
    '''x ** 0.5'''
    for x, y in values:
        v = x ** 0.5
    
def valuebuild(count,bfloat=False):
    values=[]
    while len(values)<count:
        x=random.randint(1,2000)
        y=random.randint(0,50)
        
        if bfloat:
            x+=random.random()
            y+=random.random()
        values.append( (x,y) )
    return values


def main(bfloat=False):
    if bfloat:
        print 'Testing with float values'
    else:
        print 'Testing with int values'
    
    values = valuebuild(1000000,bfloat)
    functions = [mathpowtest,builtinpowtest,builtinsqrttest,mathsqrttest]
    
    for fun in functions:
        print '%-10s : ' % fun.__doc__,
        starttime=time.time()
        fun(values)
        print time.time() - starttime
        

main()
main(True)
[/php]

---

### Post by Reiger on 2010-04-01
Depends on the underlying implementation: if x ** y simply casts input argument to float/double type in C and uses IEEE FP operations (possibly optimized using SSE) these ought to be quite fast.

However you can optimize much further if y is positive integer because you can reduce the complexity of the operation: Rather than y multiplications of x or similar; you can reduce it to lg(y) multiplications of x or similar with lg the log(y)/log(2) function.

It works by defining x^0 as 1 and computing the value of x^2 and re-using that a number of times, plus a final multiplication by x if y is odd:

Here is a haskell implementation of that:
```

pow :: Integer -> Integer -> Integer
-- base case x ^ 0 = 1
pow x 0 = 1
pow x n
    | odd  n = c * x * c
    | even n = c * c
    where
        c = pow x (n `div` 2) -- using integer division causes the value to be rounded down

```

---

### Post by casevh on 2010-04-01
There are some behind-the-scenes differences in your tests.

x ** y for integer values of x and y will calculate an integer result. Depending on the values of x and y, this might be a very large number. math.pow will convert both values to a float and then return a float result. 

Repeat your test using the modified code below. It should run faster since it eliminates a name lookup.

```

def mathpowtest(values):
    '''pow(x,y)'''
    f=math.pow
    for x, y in values:
        v = f(x,y)

def mathsqrttest(values):
    '''sqrt(x)'''
    f=math.sqrt
    for x, y in values:
        v = f(x)
```

For testing the speed of individual commands, take a look at the timeit module.

```

$ python -m timeit -s "x=1.1;y=2.2" "x**y"
1000000 loops, best of 3: 0.533 usec per loop
$ python -m timeit -s "import math;x=1.1;y=2.2" "math.pow(x,y)"
1000000 loops, best of 3: 0.82 usec per loop
$ python -m timeit -s "import math;x=1.1;y=2.2;f=math.pow" "f(x,y)"
1000000 loops, best of 3: 0.656 usec per loop

```

The syntax is -s "<setup code>" "<command to test>".

There are other performance differences depending on platform (32 vs. 64 bits) and version of Python.

casevh

---

### Post by lavinog on 2010-04-01
> **casevh said:**
> There are some behind-the-scenes differences in your tests.

x ** y for integer values of x and y will calculate an integer result. Depending on the values of x and y, this might be a very large number. math.pow will convert both values to a float and then return a float result. 


Ok, that makes a lot of sense.
It didn't occur to me that it always returned a float.

The help for pow makes it seem like the two methods are the same:
```

pow(...)
    pow(x,y)
    
    Return x**y (x to the power of y).

```

---

### Post by casevh on 2010-04-01
To clarify one more detail, there is "**" and the builtin "pow" which are roughly the same: they call the __pow__ (or __rpow__) methods of the underlying objects. 

"math.pow" specifically returns a float. "pow" and "math.pow" are NOT the same. This is one reason why "from math import *" is not recommended.

casevh

---

