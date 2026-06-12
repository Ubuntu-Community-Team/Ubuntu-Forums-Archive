---
title: "[Python] Calling parent classes"
date: 2008-11-05
forum: Programming Talk
---

### Post by cmat on 2008-11-05
I have a program structured like this...

```


class a:
    def __init__( self ):
        self.b = b(self)

    def methodA( self ):
        print "Hello, I'm a method of class A"

class b(a):
    def __init__( self, parent ):
        self.parent = parent
        self.c = c(self)

class c(b):
    def __init__( self, parent ):
        self.parent = parent
        self.methodC()

    def methodC( self, event ):
        """ I want this to call methodA in the parent of my parent class """



```

I know how to call a method of the parent class but sometimes I would like to directly call methods in classes higher up in the hierarchy. How would I go about doing this? I've read some of the books I have and I haven't found an answer.

---

### Post by unutbu on 2008-11-05
[PHP]#!/usr/bin/env python
class a(object):
    def __init__( self ):
        # Hm. This is incestuous. class a is the parent of class b. 
        # class a should not depend on class b.
        #
        # This is not illegal, but I'd think carefully to determine if 
        # this is really necessary.
        self.b = b(self)

    def methodA( self ):
        print "Hello, I'm a method of class A"

class b(a):
    def __init__( self, parent ):
        self.parent = parent
        self.c = c(self)

class c(b):
    def __init__( self, parent ):
        self.parent = parent

#         print self.__class__
# #         <class '__main__.c'>
        #
        # I'm not sure what you are intending parent to mean,
        # but if you are looking for the parent of class c, 
        # you can get this information out of self without having
        # to pass the information manually.
        # 
        # Note that class a has to be declared as
        # class a(object) for this to work.
        # see http://www.python.org/doc/newstyle/
        #

#         print self.__class__.__mro__
# #         (<class '__main__.c'>, <class '__main__.b'>, <class '__main__.a'>, <type 'object'>)
        print 'parent classes of self: ',[cls.__name__ for cls in self.__class__.__mro__]

    def methodC( self, event ):
        #
        # When you write self.methodA, the python interpreter
        # looks in self.__dict__ for a key called methodA. 
        # If it can't find such a key, it goes looking for it 
        # in each parent class listed in self.__class__.__mro__
        # If it still can't find it, it calls self.__getattribute__
        # 
        # see http://www.python.org/doc/2.5.2/ref/attribute-access.html
        #
        # The bottom line is, self.methodA() works; self will search
        # class c, then class b then class a until it finds methodA
        # 
        self.methodA()
        """ I want this to call methodA in the parent of my parent class """

c1=c('parent')
c1.methodC('event')[/PHP]
```
% test.py
parent classes of self:  ['c', 'b', 'a', 'object']
Hello, I'm a method of class A
```

---

### Post by days_of_ruin on 2008-11-05
```
class one(object):
    def foo(self):
        print "class one"

class two(one):
    def eggs(self):
        print "class two"

a = one()
b = two()
a.foo()
b.foo() # they will both print the same thing
b.eggs() # will print "class two"
```

A class will automatically have all the methods of its parents
unless you define a method with the same name.

So don't pass parent classes as arguments to classes.
fyi inheriting object isn't necessary here but it will be in python 3.0
so you might as well start doing it now.

---

### Post by cmat on 2008-11-05
The parent variable in my classes are storing the C++ pointer to the parent class. I always done it like that and it seems to be the bad way of doing things. :)

I'll give your suggestions a try and if they work it will greatly improve my productivity.

---

