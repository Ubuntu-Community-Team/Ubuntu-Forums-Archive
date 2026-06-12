---
title: "Python: List comp VS Generator Expr"
date: 2008-03-11
forum: Programming Talk
---

### Post by Wybiral on 2008-03-11
Every Python programmer knows about list comprehensions, but not everyone knows about [generator expressions]("http://www.python.org/dev/peps/pep-0289/"). In the wild I tend to see list comprehensions everywhere... But rarely ever generator expressions.

```

sum(x * x for x in (1, 2, 3, 4))
# VS
sum([x * x for x in (1, 2, 3, 4)])

```
Sure, it's only a difference using square brackets, but if you don't have to use them... Why use them? List comprehensions also have a slight bug, they leak the iterator variable out into the surrounding code:
```

>>> sum([x * x for x in (1, 2, 3, 4)])
30
>>> x + 1
5

```
As opposed to:
```

>>> sum(x * x for x in (1, 2, 3, 4))
30
>>> x + 5
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'x' is not defined

```

This issue will be fixed in Python 3000, but it looks to me like there's still no reason not to use generator expressions... So why don't I ever see them?

---

### Post by CptPicard on 2008-03-11
Look at my code and you will see them. :) I tend to write all of my python in sort of procedural list processing-style instead of object orientation... and generator expressions (and generator functions) are prevalent as it helps  save memory, although they *are* slow... (remember the all-combinations generator of mine?)

---

### Post by slavik on 2008-03-11
try to benchmark list comprehension vs. generator expression.

in Perl, many people tend to use map for loops, the problem is that map happens to return a list of whatever it processed which might be useless ...

if you want to increment every value in an array by 1, using map will not only increment the value but also create a copy for return.

examples:

$_++ for(@array);

vs

@array2 = map { $_++ } @array;

---

### Post by Wybiral on 2008-03-11
> **CptPicard said:**
> Look at my code and you will see them. :) I tend to write all of my python in sort of procedural list processing-style instead of object orientation... and generator expressions (and generator functions) are prevalent as it helps  save memory, although they *are* slow... (remember the all-combinations generator of mine?)

Indeed. I didn't use generator functions for a long time myself, but once I started playing with them I was impressed (python is the first language I've ever used that has them). Using generators is WAY more efficient than building lists/tuples everywhere when all you need is an iterator.

It's sad that I still see so much code that uses "range" for iterating integers (which in Python 3000 range will act like xrange and xrange will be no more!) or building entire lists in-place just to iterate them.

I was apprehensive about Python 3000 changing all the list-building builtins to generators at first (like map, filter, range, ...), but I get it now... It's definitely for the better. And if you need a list, you can always just use list(generator).

Personally I feel like list comprehension itself should be done away with and replaced with list(generator expression). And if it has any performance drawbacks, I'm sure they could detect that it's just a list comprehension and do whatever optimizations they need.

---

### Post by CptPicard on 2008-03-11
> **Wybiral said:**
>  (python is the first language I've ever used that has them).

One of the reasons I favour Scheme over Common Lisp is that Scheme has a "yield" function that returns whatever you're evaluating in a nice package for later application of "force" that continues the evaluation. It's essentially the same thing, so I really like seeing it in Python -- expressing computations in terms of lazy lists is cool. Python's generators are not quite the real deal though, as the underlying language primitive is the full continuation, which Python (and CL) lacks...


> 
Personally I feel like list comprehension itself should be done away with and replaced with list(generator expression).

Well, that is what it essentially syntactically looks like to me already as it is -- I don't know how different the implementation is. And [] is nice syntactic sugar for list().

---

### Post by Wybiral on 2008-03-11
> **CptPicard said:**
> Well, that is what it essentially syntactically looks like to me already as it is -- I don't know how different the implementation is. And [] is nice syntactic sugar for list().

It is a bit shorter, but IMO it's one of the few things in Python that breaks the rules... It allows for multiple ways to do the same thing, and it's not a congruent behavior with other types.

For instance, why can't I use this:
```

{key:value for key, value in sequence}
# Or even this...
{(key, value) for key, value in sequence}

```

Dict comprehensions were actually consider in [PEP 274]("http://www.python.org/dev/peps/pep-0274/"), but they decided that dict(generator expression) was a better way to do it.

With generator expressions, everything is the same.
You can do this:
```

dict((key, value) for key, value in sequence)
list((key, value) for key, value in sequence)
tuple((key, value) for key, value in sequence)
set((key, value) for key, value in sequence)

```
And everything just works exactly like you would expect it to (no discrimination between types).

---

### Post by CptPicard on 2008-03-11
I would probably have preferred the alternative and making generator expressions play nicely with [] and {}. Explicitly spelling out "list" etc. is problematic because it breaks the "wysiwygness" of what you're writing... a common representation for list is [a,b,c] both in Python output and in code. You don't typically create lists by stating something like list(a,b,c), nor is it printed like that...

Generating into tuples would be problematic though because of the ambiguity of ().

---

### Post by Wybiral on 2008-03-12
> **CptPicard said:**
> Generating into tuples would be problematic though because of the ambiguity of ().

That's part of my problem with having list comp and generator expressions both. If tuples are represented with "()" and lists with "[]" then they should be almost interchangeable (aside from "()" also being used to denote a statement as most languages do).

```

>>> [x * 2 for x in xrange(10)]
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
>>> (x * 2 for x in xrange(10))
<generator object at 0xb7dbcb4c>
>>> list(x * 2 for x in xrange(10))
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
>>> tuple(x * 2 for x in xrange(10))
(0, 2, 4, 6, 8, 10, 12, 14, 16, 18)

```

---

### Post by pmasiar on 2008-03-12
I am not sure if it is relevant here, but list are mutable and tuples are not.

---

### Post by CptPicard on 2008-03-20
Just thought to necro this thread for a little comment on how totally excellent the generator expressions and the associated iterator protocol for objects really is. Duck typing at its best.

I am currently writing a stock market analysis toolkit for myself -- I am eventually planning on publishing a list of current, interesting heads-up indicators on a web page. Technical analysis indicators of the stock market are essentially time series filters, that take other time series and transform them in some way. The underlying primary time series is of course usually the stock price.

I also have a multi-gigabyte database with stock market data from 1970 onwards. Good for backtesting and interesting history analysis (such as pattern matching and seeing if anything can be inferred of historical development of the shapes of recent price curves).

So essentially I have a lower-level library that hooks into the database and has generator functions for the various time-series, and slightly higher level classes that describe the time series interface -- the ultimate goal is to be able to nest them pretty arbitrarily to quickly test new indicators. All of them are iterators... so they read other iterators and produce new iterator values... the database is pretty completely abstracted away, and writing a new indicator on top of the old ones is just a couple of lines of code.... on top of the base library which is just a few hundred lines. :)

I'm really starting to like Python more and more... ;)

---

### Post by Wybiral on 2008-03-20
I too am falling in love with how little code I am able to express the same concepts with in Python (as compared to other languages I've used). The less I have to type, the happier I am :)

What are you using to interface with the lower-level library? I used to advocate SWIG / PyRex, but I've recently been using the ctypes module quite a bit and it's great how simple it is.

---

### Post by CptPicard on 2008-03-20
No, the lower-level doesn't mean C or anything. It's just a set of Python primitives (read: generator functions) that help me produce the series I need, and I also keep the db-specific stuff there. So essentially I yield() stuff from cursor. I just then wrap them with my Signal class.. :) I haven't quite decided on the proper interface though.

Should also add that Python is great for exploratory prototyping. I really need to know there is *something there* in my data before I invest my time in optimization...

---

### Post by Wybiral on 2008-03-21
I totally agree about Python being a good prototyping language. You can make full use of its high-level constructs to write the solution as quickly as possible just to make sure your solution is even going to work. Then you have a few choices if you find you need more speed.

[LIST=1]
[*]Write highly profiled, "tight" code in C and use SWIG / PyRex / ctypes to call it from Python
[*]Use something like [psyco]("http://psyco.sourceforge.net/") to do the optimizing for you!
[*]Rewrite the Python code itself to be more efficient (there are some tricks like not using global functions or aliasing class method accesses with a local variable)
[/LIST]

One reason I have found not to use generators is when you need to optimize something using psyco, which btw does a really good job speeding up tight loops in Python. Usually it's not too hard to change things around a bit to make psyco work better (most of the time you don't have to, but when speed really matters certain changes will make psyco optimize more efficiently), but you will have to rewrite your code that uses generators (and I'm sure they'll eventually find a way to optimize them too).

---

