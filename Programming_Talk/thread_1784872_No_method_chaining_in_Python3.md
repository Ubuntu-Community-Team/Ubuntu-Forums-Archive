---
title: "No method chaining in Python3?"
date: 2011-06-17
forum: Programming Talk
---

### Post by skytreader on 2011-06-17
I'm confused at this behavior from Python3.

```
>>> eggs = list(range(3))
>>> eggs
[0, 1, 2]
>>> eggs.reverse()
>>> eggs
[2, 1, 0]
>>> eggs = list(range(3)).reverse()
>>> eggs
>>> print("Nothing appeared?")
Nothing appeared?

```

So method chaining is no longer supported in Python3? Or is there something special with lists? I don't think this was mentioned in [this document]("http://docs.python.org/release/3.0.1/whatsnew/3.0.html"). Does anyone know where this is documented so I won't stumble upon things like this in the future?

Thanks!

---

### Post by cgroza on 2011-06-17
I get the same behavior in python 2.7. This happens because lists are mutable and reverse returns None. So, eggs == None after that expression is evaluated.


It is perfect legal python...

---

### Post by Simian Man on 2011-06-17
That doesn't work in Python 2 either.  The issuse is that the reverse function does it's reversal in place and doesn't return anything.  So when you assign it to eggs, you overwrite the list you had built.

---

