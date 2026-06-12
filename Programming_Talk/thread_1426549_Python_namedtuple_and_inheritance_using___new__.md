---
title: "Python namedtuple and inheritance using __new__"
date: 2010-03-10
forum: Programming Talk
---

### Post by CHW on 2010-03-10
Hello,

I want to use the following code:

[PHP]
class Test(tuple):
    def __new__(self, n=None, k=None, d=None):
        # t = do some processing...
        return tuple.__new__(self,t)

    def __call__(self, c):
        return c*2
[/PHP]

This works as expected, I can create a tuple and call it.

For better readability I would like to use a namedtuple, but here I fail.

I found one method on the python.org site, which is callable, but I don't manage to define __new__ to be able to make some input processing.

[PHP]class Point(collections.namedtuple('Point', 'x y')):
    def __call__(self,x):
        return x*2
[/PHP]

I tried around and managed to "inherit" a namedtuple using the __new__ method:

[PHP]class Test(tuple):
    
    def __new__(self, n=None, k=None, d=None):
        cpara = collections.namedtuple('Foo', 'n, k, d')
        # t = some processing...
        return cpara._make(t)
      
    def __call__(self, c):
        c*2[/PHP]

Well, here I get the namedtuple I would like to have, but the object is not callable...

Does anyone knows how to solve this issue?

Regards,
CHW

---

### Post by nvteighen on 2010-03-10
What are you trying to do, exactly? __new__ shouldn't ever be touched... and __call__ is used for enabling the object to be called as a function (syntactically, i.e. as "blah(something)").

Inheritance should work by just using __init__ (and calling the super class's __init__ to initialize its variables), nothing else. And if you want to have this new type make something, create a method, don't touch __call__ unless you really want to create something callable (which is pretty strange...).

---

### Post by CHW on 2010-03-11
After some more thinking I found a solution. It's more or less that what I wanted:
[PHP]class Foo(collections.namedtuple('Foo', 'x y z')):
    pass    

class FooTest(Foo):
    def __new__(self, n=None, k=None, d=None):
        # do some processing...
        return Foo.__new__(self,n,k,d)
    
    def __call__(self, c):
        return c*2[/PHP]

> **nvteighen said:**
> What are you trying to do, exactly? __new__ shouldn't ever be touched... and __call__ is used for enabling the object to be called as a function (syntactically, i.e. as "blah(something)").

Inheritance should work by just using __init__ (and calling the super class's __init__ to initialize its variables), nothing else. And if you want to have this new type make something, create a method, don't touch __call__ unless you really want to create something callable (which is pretty strange...).

Yes, I want to create a callable container of type namedtuple.

It may look strange, but in a first prototype of my module I had two separate classes, a callable and a container class, but it makes sense for me to merge them.

I have also good reasons for using __new__, for example if you would like to create the class of integers modulo p it makes also sense to use __new__:

[PHP]
class Intmod(int):
   def __new__(self,i,p):
      return int.__new__(self,i%p)
[/PHP]

---

### Post by scott.enderle on 2011-01-23
> **nvteighen said:**
> What are you trying to do, exactly? __new__ shouldn't ever be touched...

This is a stale thread but I have to correct this!

How could you subclass a tuple without touching __new__? Tuples are immutable -- can't be changed once they're created. __init__ can't do anything to a tuple once created.

---

