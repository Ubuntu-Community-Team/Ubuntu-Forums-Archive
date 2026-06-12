---
title: "python call a function whose name is stored in a variable"
date: 2009-03-30
forum: Programming Talk
---

### Post by giuspen on 2009-03-30
is it possible in python to call a function whose name is stored in a variable?
I explain better: I have a module MODULE with many many functions and actually I have an "if... elsif... elsif..." which calls the function A if in a variable VAR there's A, calls B if in the variable VAR there's B and so on.
Is it possible to do something like MODULE.VAR()?
Thanks in advance,
Giuseppe.

---

### Post by Zugzwang on 2009-03-30
There's the eval()-function, but use it with care as it is very simple to introduce security problems into your program with it.

Most of the situations in which you have some problem like this can be resolved using polymorphism (in object oriented programming), see [here]("http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming") for examples.

---

### Post by ghostdog74 on 2009-03-30
```

>>> def f(a,b):
...  return a+b
...
>>> a=f
>>> globals()['a'](1,2)
3


```

---

### Post by unutbu on 2009-03-30
If the function f is defined in amodule.py, then you can access it with
[PHP]
import amodule
varstring='f'
function=getattr(amodule,varstring)
function()
[/PHP]

---

### Post by giuspen on 2009-03-30
> **unutbu said:**
> If the function f is defined in amodule.py, then you can access it with
[PHP]
import amodule
varstring='f'
function=getattr(amodule,varstring)
function()
[/PHP]

The function getattr is exactly what I was searching for.
Thanks again,
Giuseppe.

---

