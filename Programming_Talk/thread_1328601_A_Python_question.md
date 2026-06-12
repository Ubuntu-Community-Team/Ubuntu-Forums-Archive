---
title: "A Python question"
date: 2009-11-16
forum: Programming Talk
---

### Post by C++buntu on 2009-11-16
Hi everyone,

I define a little function in Python like this:

```

def f(t, T):
    if 0 < t < T/2.0:
        value = 1.0
    elif t == T/2.0:
        value = 0.0
    elif T/2.0 < t < float(T):
        value = -1.0
    return value

```And when i run this in IPython, I obtain the following error:

[html]
---------------------------------------------------------------------------
UnboundLocalError                         Traceback (most recent call last)

/home/cppbuntu/Desktop/Python/Problems/Chapter 02/<ipython console> in <module>()

/home/cppbuntu/Desktop/Python/Problems/Chapter 02/<ipython console> in f(t, T)

UnboundLocalError: local variable 'value' referenced before assignment
[/html]I don't understand...how can the variable 'value' be referenced before assignment in this code?

Thanks for the help.

---

### Post by tribaal on 2009-11-16
Ah, classical mistake :)

Simply put, if the code passes in no branch, you ask python to return "value" when it has not been defined.

Probably your second "elif" statement should be an "else" statement (so as to catch all cases), or even better, you should declare your "value" variable before entering the conditional part of the code (i.e. before "if").
Assign it to be "None" if you can't think of any sensible default value.

Here's your code, corrected:

```

def f(t, T):
    value = 0
    if 0 < t < T/2.0:
        value = 1.0
    elif t == T/2.0:
        value = 0.0
    elif T/2.0 < t < float(T): #Maybe if could simply be "else:"?
        value = -1.0

    return value
```

---

### Post by Rinzwind on 2009-11-16
When variables are assigned inside a function, they are always bound to the function's **local namespace**. The global namespace is never checked for 'value', hence the error. Your if's misses an else to catch all branches of the if.

damn I lost to tribaal :D

---

### Post by Can+~ on 2009-11-16
[PHP]elif t == T/2.0:[/PHP]

Aside from what has been said above, you should NEVER compare floats directly, not in python, not in C/C++, not in Java, never (int and decimal are fine).

Why? Because of the specification of [floating point by the IEEE]("http://en.wikipedia.org/wiki/IEEE_754-1985"), floats are never accurate, as simple as doing:

[PHP]>>> 1.1 + 2.0
3.1000000000000001[/PHP]

Leads to unexpected errors, floats must be used inside ranges.

*edit:
If you care for precision, then use the [Decimal module (Fixed point)]("http://docs.python.org/library/decimal.html"). But it seems that you're working on things related to physics, so stick with float, but test within ranges as I told you before, as computational error are minimal compared to real life measurement errors (unless you count going out of range, overflows, etc)

---

### Post by C++buntu on 2009-11-16
So many thanks to all of you! Good explanations! Very appreciated.

---

### Post by C++buntu on 2009-11-16
So, you test for what?
elif abs(t - T/2.0) < 1e-6:
    <statements>
doesn't work either...i need that my function f(t, 2) return the value 0.0 when t = 1.0...

---

### Post by Can+~ on 2009-11-16
[PHP]def feq(a, b, epsylon=0.000001):
	return abs(a - b) < epsylon[/PHP]

So now:

[PHP]feq(0.1, 0.10000001) # yields true[/PHP]

---

### Post by C++buntu on 2009-11-16
Yeah, that's exactly what i've done...

```

def f(t, T):
    if 0 < t < T/2.0:
        value = 1.0
    elif T/2.0 < t < float(T):
        value = -1.0
    elif abs(t - T/2.0) < 1e-6:
        value = 0.0
    else:
        value = 0.0
    return value

# i know that i can use the numpy module...
# but for this problem, it's supposed that we don't know yet ;)
def makelist(start, stop, inc):
    val = start
    tmp   = []
    while val <= (stop + inc):
        tmp.append(val)
        val += inc
    return tmp
    
for t in makelist(0, 2.5, 0.1):
    print '%5.2f\t%5.2f' % (t, f(t, 2))

```

The result of this is

[HTML]
 0.00     0.00
 0.10     1.00
 0.20     1.00
 0.30     1.00
 0.40     1.00
 0.50     1.00
 0.60     1.00
 0.70     1.00
 0.80     1.00
 0.90     1.00
 1.00     1.00 # supposed to be 0.0!
 1.10    -1.00
 1.20    -1.00
 1.30    -1.00
 1.40    -1.00
 1.50    -1.00
 1.60    -1.00
 1.70    -1.00
 1.80    -1.00
 1.90    -1.00
 2.00     0.00
 2.10     0.00
 2.20     0.00
 2.30     0.00
 2.40     0.00
 2.50     0.00
[/HTML]

What i'm missing?

---

### Post by WitchCraft on 2009-11-17
C++ has a definition for the machine epsilon, you might use that one.

---

### Post by Arndt on 2009-11-17
> **C++buntu said:**
> Yeah, that's exactly what i've done...

```

def f(t, T):
    if 0 < t < T/2.0:
        value = 1.0
    elif T/2.0 < t < float(T):
        value = -1.0
    elif abs(t - T/2.0) < 1e-6:
        value = 0.0
    else:
        value = 0.0
    return value

# i know that i can use the numpy module...
# but for this problem, it's supposed that we don't know yet ;)
def makelist(start, stop, inc):
    val = start
    tmp   = []
    while val <= (stop + inc):
        tmp.append(val)
        val += inc
    return tmp
    
for t in makelist(0, 2.5, 0.1):
    print '%5.2f\t%5.2f' % (t, f(t, 2))

```

The result of this is

[HTML]
 0.00     0.00
 0.10     1.00
 0.20     1.00
 0.30     1.00
 0.40     1.00
 0.50     1.00
 0.60     1.00
 0.70     1.00
 0.80     1.00
 0.90     1.00
 1.00     1.00 # supposed to be 0.0!
 1.10    -1.00
 1.20    -1.00
 1.30    -1.00
 1.40    -1.00
 1.50    -1.00
 1.60    -1.00
 1.70    -1.00
 1.80    -1.00
 1.90    -1.00
 2.00     0.00
 2.10     0.00
 2.20     0.00
 2.30     0.00
 2.40     0.00
 2.50     0.00
[/HTML]

What i'm missing?

Put a print statement in each branch of f and see which path the execution takes.

(Was this solved? Is it unsolved again?)

---

### Post by Tony Flury on 2009-11-17
I think maybe the source of your error now is that you have used the epsillon idea when comparing equalities but not when comparing inequalities.

```

def f(t, T):
    if 0 < t < T/2.0:
        value = 1.0
    elif T/2.0 < t < float(T):
        value = -1.0
    elif abs(t - T/2.0) < 1e-6:
        value = 0.0
    else:
        value = 0.0
    return value

```

T/2.0 is a float - which should be 1.000000 (exactly) but due to rounding etc might come out as 1.0000000001 and so t is actually smaller then t/2.0 - hence your answer.

I would do something like this - build a generic compare function that uses the espillion error value.

```

import math

eps = 1e-6

def cmp(a,b,e)
    diff = a-b
    if diff > e:
        # a > b within the error e
        return 1
    if diff < -e:
        # a < b within the error e
        return -1
    if fabs(diff) < e
        # a == b within the error e
        return 0

def f(t, T):
     # 0 < t < T/2.0
    if (cmp(t,0,eps) == 1) and (cmp(t, T/2.0, eps) == -1):
        value = 1.0
    # T/2.0 < t < float(T)
    elif (cmp(t,T/2.0,eps) ==1) and (cmp(t,float(T),eps) == -1): 
        value = -1.0
    # T/2.0 == t
    elif (cmp(t, T/2.0, eps) == 0):
        value = 0.0
    else:
        value = 0.0
    return value

```

You may need to test all of that, but it should work. It also can probably be shortened, but it is long hand to help you understand what it does (and that is shorthand for I am too lazy to optimise it ;-) ).

An even more python esque way to do things would be to create a new class, that extends float and allows for the setting of an espillon value for the use of comparisons, and then overriding the comparison operators so that it uses the epsillon error value if it has been set - that is left as an exercise for the reader.

---

### Post by Can+~ on 2009-11-17
As for creating a float range, (aside from having the numpy), you can do:

[PHP]def frange(start, stop, inc):
	val = start
	while val <= (stop + inc):
		yield val
		val += inc[/PHP]

Which is your algorithm, although translated to "yield", so it doesn't need a list, it just freezes the content inside the function.

Alternatively, create a list and multiply it:
[PHP]>>> map(lambda x: x*0.10, [i for i in xrange(0, 10)])
[0.0, 0.10000000000000001, 0.20000000000000001, 0.30000000000000004, 0.40000000000000002, 0.5, 0.60000000000000009, 0.70000000000000007, 0.80000000000000004, 0.90000000000000002][/PHP]

---

