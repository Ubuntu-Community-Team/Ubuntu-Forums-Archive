---
title: "python print statement"
date: 2010-05-07
forum: Programming Talk
---

### Post by cybo on 2010-05-07
i'm somewhat new to python.

i need to print a sequence of numbers without any spaces between them. the code must be in python. 

i'm doing something like:

```
#!/usr/bin/python

for i in range(1, 10):
  print i,
```

however the result i get is
1 2 3 4 5 6 7 8 9 10

how do i make it look like
12345678910

help is appreciated.

---

### Post by Queue29 on 2010-05-07
In python3 it would be
```
print(i, sep='')
```

I guess you could get that functionality with 
```
from __future__ import print_function
```

---

### Post by wmcbrine on 2010-05-07
I'd use sys.stdout.write().

---

### Post by StephenF on 2010-05-07
print "".join(str(x) for x in range(1, 10))

---

### Post by soltanis on 2010-05-08
You need []'s

```

pring "".join([str(x) for x in range(10)])

```

Alternatively just use sys.stdout.write like this:

```

[sys.stdout.write(str(x)) for x in range(10)]

```

Python gives you one way to write loops in shorthand, and I abuse it often.

---

### Post by StephenF on 2010-05-08
> **soltanis said:**
> You need []'s
It runs without them, and faster. There is also the advantage that generator expressions don't leak the x out into the local namespace.

---

### Post by cybo on 2010-05-08
> **StephenF said:**
> It runs without them, and faster. There is also the advantage that generator expressions don't leak the x out into the local namespace.

can you explain what are you trying to say? i'm not a novice programmer but not an expert either.

---

### Post by snova on 2010-05-08
> **soltanis said:**
> ```

[sys.stdout.write(str(x)) for x in range(10)]

```

Python gives you one way to write loops in shorthand, and I abuse it often.

Ew. Generating a completely useless list solely for its side-effects isn't what I would call nice.

> **cybo said:**
> can you explain what are you trying to say? i'm not a novice programmer but not an expert either.

```

>>> "".join(str(x) for x in range(10))
'0123456789'
>>> x
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'x' is not defined
>>> "".join([str(x) for x in range(10)])
'0123456789'
>>> x
9
>>>

```

In the first example, **x** is only visible in the generator expression- after it completes, **x** no longer exists. In the second (a list comprehension), the last value of **x** sticks around and can still be used/abused.

The disadvantages to that is you can overwrite something in the enclosing scope; generators won't do this:

```

>>> y = 'foo'
>>> "".join(str(y) for y in range(10))
'0123456789'
>>> y
'foo'
>>> 

```

Generators are usually preferred unless you actually need a list.

---

### Post by StephenF on 2010-05-09
> **snova said:**
> Generators are usually preferred unless you actually need a list.
With that in mind xrange should be used in preference to range. Also, you can make a list using a generator expression, similarly, a tuple.
```

>>> list(x for x in xrange(1, 10))
[1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> x
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'x' is not defined
>>> 

```

---

### Post by soltanis on 2010-05-09
> **snova said:**
> Ew. Generating a completely useless list solely for its side-effects isn't what I would call nice.


This is what happens when you try to yield Python like a LISP. Bad things, apparently.

I find it rather odd that x is dumped into the local namespace. Guess I finally sympathize with that Perl programmer who complained about Python's scoping rules.

---

### Post by StephenF on 2010-05-09
> **soltanis said:**
> I find it rather odd that x is dumped into the local namespace.
It's fixed in Python 3 so there's that.

---

### Post by Can+~ on 2010-05-09
Answering the OP:

Python2.x has no way to achieve this with the print statement (or it has, but I forgot), one of the many reasons they decided to ditch it in favor of "print function" in python3.

Using the join trick is, IMO, the best way to achieve it; and the difference between the internal definition of each one:

[PHP]>>> # Similar to just doing x = range(0, 100, 2) in python2.6
>>> x = [i for i in xrange(0, 100, 2)]
>>> x
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98]
>>> # Similar to just doing x = xrange(0, 100, 2) in python2.6, range in python3
>>> x = (i for i in xrange(0, 100, 2))
>>> x
<generator object <genexpr> at 0x7fe16cfabf00>[/PHP]

There are many issues about each one, but the main (dis)advantage for each one, is that square brackets immediately computes the result and stores in memory, whereas a generator expression is pretty much a function that generates it when called (in python world, that means that has passes the duck-typed existence test of next() method)

Any programmer would see the differences with this, pre-computing wastes CPU now instead of doing it later, but uses up more space. On the other hand, creating a generator expressions saves up memory, but needs a new cycle to be computed each time it's called.

So, in the eyes of the beginner, it has no semantical difference.

In fact, python works with both definitions equally. A list knows how to be iterated, a generator expression also knows how to be iterated. When the join method transverses the given argument, it will just go through the iterative method. Plain simple polymorphism in a dynamically-typed world.

---

### Post by soltanis on 2010-05-10
You know, I never did like the suggestion that list comprehensions were better or easier to read than map, filter, and lambda.

In any case, if any statement that looks like "x for x in y" is a generator expression, does that mean I can put any iterable object between a set of []'s and make it a list?

---

### Post by wmcbrine on 2010-05-10
Not quite... you're going to want to use list() in those situations:

list('hello')
list(xrange(5))

The comparable list comprehensions would be:

[i for i in 'hello']
[i for i in xrange(5)]

(Of course range(5) would be more sensible, in Python 2.x. In Python 3.x, there is no xrange(), but something like the above is required to make an actual list from range().)

---

### Post by snova on 2010-05-10
> **soltanis said:**
> You know, I never did like the suggestion that list comprehensions were better or easier to read than map, filter, and lambda.

In any case, if any statement that looks like "x for x in y" is a generator expression, does that mean I can put any iterable object between a set of []'s and make it a list?

```
x for x in xrange(10)
```

Is a generator when put between **()**, a list comprehension when put between **[]**, and if you use it as a function argument it's also a generator:

[PHP]
>>> def foo(*args): print args
... 
>>> foo(z for z in [1, 2, 3])
(<generator object <genexpr> at 0x8aac0cc>,)
>>> foo(z for z in [1, 2, 3], 2)
  File "<stdin>", line 1
SyntaxError: Generator expression must be parenthesized if not sole argument
>>>
[/PHP]

As to list comprehensions vs. map/filter/lambda, well, take your pick:

[php]
odd_numbers = [n for n in range(100) if n % 2]
odd_numbers = filter(lambda n: n % 2, range(100)
[/php]

I like the "flow" of the list comprehension- "for n in a range of numbers, take n if n % 2". I don't think lambda's are as elegant in this case- for one thing, I tend to have trouble isolating them visually (where does it end? there are no clear borders).

As to map, I mostly like it in simpler cases, such as converting a list of objects to a different type:

[php]
numbers = map(str, range(10)) # Any simple function would do
numbers = [str(n) for n in range(10)]
[/php]

Whether or not a list comprehension is still nicer probably depends on the programmer. It seems to me the latter is a little visually busy for such a simple operation. (In addition, since there's no Python code to be executed here, the map version will technically run very slightly faster. This is a disadvantage of lambda's that list comprehensions do not share to the same extent.)

---

