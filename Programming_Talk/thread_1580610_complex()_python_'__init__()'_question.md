---
title: "complex(?) python '__init__()' question"
date: 2010-09-23
forum: Programming Talk
---

### Post by daweefolk on 2010-09-23
When writing up the __init__() function for a class in python, is there a way to make it so the object can have UP TO a certain number of arguments?
like if i wanted a class to be able to have arg1,arg2, and arg3 assigned in the __init__ function but not require all three. (say one object only needed arg1 and arg2 but the next one needed three)
Or does python absolutely require all the arguments?
Fairly new python programmer here, be gentle please

---

### Post by schauerlich on 2010-09-23
Accept a variable number of arguments, and then raise an error if they give too many:

```
>>> class Foo:
...     def __init__(self, *args):
...             if len(args) > 3:
...                     raise TypeError("takes at most 3 arguments (%d given)" % len(args))
... 
>>> Foo(1,2,3)
<__main__.Foo instance at 0x6363f0>
>>> Foo(1,2,3,4,5)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 4, in __init__
TypeError: takes at most 3 arguments (5 given)
>>> 

```

In this instance, adding *args to the parameter list means that all of the parameters are passed to __init__() as a list. You can unpack them from there. 

You might also be able to achieve the effect you want with keyword arguments:

```
>>> class Foo:
...     def __init__(self, arg1=None, arg2=None, arg3=None):
...             print [arg1, arg2, arg3]
... 
>>> Foo(1, 2)
[1, 2, None]
<__main__.Foo instance at 0x636378>
>>> Foo(1, arg3=6)
[1, None, 6]
<__main__.Foo instance at 0x6363c8>
>>> Foo(arg2=12, arg3=6)
[None, 12, 6]
<__main__.Foo instance at 0x636378>

```

---

### Post by Bachstelze on 2010-09-23
You can put defaults values to arguments:

def __init__(self, arg1=None, arg2=None, arg3=None):

Then you can call it with

Class('foo') #arg2 and arg3 will be None
Class('foo', 'bar') #arg3 will be None
Class('foo', 'bar', 'baz')
Class(arg2='foo') #arg1 and arg3 will be None

Etc.

---

### Post by daweefolk on 2010-09-23
thanks schauerlich! That's EXACTLY what I wanted! This is why i love these forums. fast, amazing replies.

---

