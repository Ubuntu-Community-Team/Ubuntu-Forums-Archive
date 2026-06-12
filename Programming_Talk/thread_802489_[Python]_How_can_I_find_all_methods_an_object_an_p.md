---
title: "[Python] How can I find all methods an object an perform?"
date: 2008-05-21
forum: Programming Talk
---

### Post by unutbu on 2008-05-21
I'm trying to learn Python. I am struggling with finding good documentation on what methods an object can perform. (And what data structures it contains as well).

For example,

```
from optparse import OptionParser
parser = OptionParser()
parser.add_option("--symbol", dest="symbol", help="ticker symbol, e.g. IBM")
parser.add_option("--form", dest="form", help="'10-K' is the default")

(opt, args) = parser.parse_args()

# for option,val in opt.iteritems:
#     print option,val
help(opt)

```

I wanted to iterate through all the options passed to opt using the commented out lines, but of course they don't work because opt is not a hash.

I tried looking at help(opt), but I don't understand the output help is giving. 

What do the underscores mean?
Is there a python equivalent of perldoc?
How do I iterate over the options in opt?

---

### Post by LaRoza on 2008-05-21
> **unutbu said:**
> 
What do the underscores mean?
Is there a python equivalent of perldoc?
How do I iterate over the options in opt?

I just ran:
```

help(optparse)

```

It gave a lot of information. 

Underscores are "private" variables/methods.

There are doc strings.

---

### Post by unutbu on 2008-05-21
It appears opt is a Values object.
```
    class Values
     |  Methods defined here:
     |  
     |  __cmp__(self, other)
     |  
     |  __init__(self, defaults=None)
     |  
     |  __repr__ = _repr(self)
     |  
     |  __str__(self)
     |  
     |  ensure_value(self, attr, value)
     |  
     |  read_file(self, filename, mode='careful')
     |  
     |  read_module(self, modname, mode='careful')
```

(Q1) Where can I go to find out what ensure_value, read_file and read_module do?

Also, I happened to try
```
print str(opt)
```

and got 

```
{'symbol': 'IBM', 'form': None}
```

Too bad this is a string and not a true hash.

(Q2) How could I have known apriori that str can operate on a Values object? 

(Q3) Where is it documented how str behaves when fed a Values object?

(Q4) How can I turn the string str(opt) into a hash?

(Q5) Is Values a subclass of some other class? How can I find that out, so I can explore what methods opt gains through inheritance?

(Q6) When I typed help(opt) I got

```
Help on instance of Values in module optparse object:

class instance(object)
 |  instance(class[, dict])
 |  
 |  Create an instance without calling its __init__() method.
 |  The class must be a classic class.
 |  If present, dict must be a dictionary or None.
 |  
 |  Methods defined here:
 |  
 |  __abs__(...)
 |      x.__abs__() <==> abs(x)
 |  
 |  __add__(...)
 |      x.__add__(y) <==> x+y
 |  
 |  __and__(...)
 |      x.__and__(y) <==> x&y
 |  
 |  __call__(...)
 |      x.__call__(...) <==> x(...)
 |  
 |  __cmp__(...)
 |      x.__cmp__(y) <==> cmp(x,y)
 |  
 |  __coerce__(...)
 |      x.__coerce__(y) <==> coerce(x, y)
 |  
 |  __contains__(...)
 |      x.__contains__(y) <==> y in x
 |  
 |  __delattr__(...)
 |      x.__delattr__('name') <==> del x.name
 |  
 |  __delitem__(...)
 |      x.__delitem__(y) <==> del x[y]
 |  
 |  __delslice__(...)
 |      x.__delslice__(i, j) <==> del x[i:j]
 |      
 |      Use of negative indices is not supported.
 |  
 |  __div__(...)
 |      x.__div__(y) <==> x/y
 |  
 |  __divmod__(...)
 |      x.__divmod__(y) <==> divmod(x, y)
 |  
 |  __eq__(...)
 |      x.__eq__(y) <==> x==y
 |  
 |  __float__(...)
 |      x.__float__() <==> float(x)
 |  
 |  __floordiv__(...)
 |      x.__floordiv__(y) <==> x//y
 |  
 |  __ge__(...)
 |      x.__ge__(y) <==> x>=y
 |  
 |  __getattribute__(...)
 |      x.__getattribute__('name') <==> x.name
 |  
 |  __getitem__(...)
 |      x.__getitem__(y) <==> x[y]
 |  
 |  __getslice__(...)
 |      x.__getslice__(i, j) <==> x[i:j]
 |      
 |      Use of negative indices is not supported.
 |  
 |  __gt__(...)
 |      x.__gt__(y) <==> x>y
 |  
 |  __hash__(...)
 |      x.__hash__() <==> hash(x)
 |  
 |  __hex__(...)
 |      x.__hex__() <==> hex(x)
 |  
 |  __iadd__(...)
 |      x.__iadd__(y) <==> x+y
 |  
 |  __iand__(...)
 |      x.__iand__(y) <==> x&y
 |  
 |  __idiv__(...)
 |      x.__idiv__(y) <==> x/y
 |  
 |  __ifloordiv__(...)
 |      x.__ifloordiv__(y) <==> x//y
 |  
 |  __ilshift__(...)
 |      x.__ilshift__(y) <==> x<<y
 |  
 |  __imod__(...)
 |      x.__imod__(y) <==> x%y
 |  
 |  __imul__(...)
 |      x.__imul__(y) <==> x*y
 |  
 |  __index__(...)
 |      x[y:z] <==> x[y.__index__():z.__index__()]
 |  
 |  __int__(...)
 |      x.__int__() <==> int(x)
 |  
 |  __invert__(...)
 |      x.__invert__() <==> ~x
 |  
 |  __ior__(...)
 |      x.__ior__(y) <==> x|y
 |  
 |  __ipow__(...)
 |      x.__ipow__(y) <==> x**y
 |  
 |  __irshift__(...)
 |      x.__irshift__(y) <==> x>>y
 |  
 |  __isub__(...)
 |      x.__isub__(y) <==> x-y
 |  
 |  __iter__(...)
 |      x.__iter__() <==> iter(x)
 |  
 |  __itruediv__(...)
 |      x.__itruediv__(y) <==> x/y
 |  
 |  __ixor__(...)
 |      x.__ixor__(y) <==> x^y
 |  
 |  __le__(...)
 |      x.__le__(y) <==> x<=y
 |  
 |  __len__(...)
 |      x.__len__() <==> len(x)
 |  
 |  __long__(...)
 |      x.__long__() <==> long(x)
 |  
 |  __lshift__(...)
 |      x.__lshift__(y) <==> x<<y
 |  
 |  __lt__(...)
 |      x.__lt__(y) <==> x<y
 |  
 |  __mod__(...)
 |      x.__mod__(y) <==> x%y
 |  
 |  __mul__(...)
 |      x.__mul__(y) <==> x*y
 |  
 |  __ne__(...)
 |      x.__ne__(y) <==> x!=y
 |  
 |  __neg__(...)
 |      x.__neg__() <==> -x
 |  
 |  __nonzero__(...)
 |      x.__nonzero__() <==> x != 0
 |  
 |  __oct__(...)
 |      x.__oct__() <==> oct(x)
 |  
 |  __or__(...)
 |      x.__or__(y) <==> x|y
 |  
 |  __pos__(...)
 |      x.__pos__() <==> +x
 |  
 |  __pow__(...)
 |      x.__pow__(y[, z]) <==> pow(x, y[, z])
 |  
 |  __radd__(...)
 |      x.__radd__(y) <==> y+x
 |  
 |  __rand__(...)
 |      x.__rand__(y) <==> y&x
 |  
 |  __rdiv__(...)
 |      x.__rdiv__(y) <==> y/x
 |  
 |  __rdivmod__(...)
 |      x.__rdivmod__(y) <==> divmod(y, x)
 |  
 |  __repr__(...)
 |      x.__repr__() <==> repr(x)
 |  
 |  __rfloordiv__(...)
 |      x.__rfloordiv__(y) <==> y//x
 |  
 |  __rlshift__(...)
 |      x.__rlshift__(y) <==> y<<x
 |  
 |  __rmod__(...)
 |      x.__rmod__(y) <==> y%x
 |  
 |  __rmul__(...)
 |      x.__rmul__(y) <==> y*x
 |  
 |  __ror__(...)
 |      x.__ror__(y) <==> y|x
 |  
 |  __rpow__(...)
 |      y.__rpow__(x[, z]) <==> pow(x, y[, z])
 |  
 |  __rrshift__(...)
 |      x.__rrshift__(y) <==> y>>x
 |  
 |  __rshift__(...)
 |      x.__rshift__(y) <==> x>>y
 |  
 |  __rsub__(...)
 |      x.__rsub__(y) <==> y-x
 |  
 |  __rtruediv__(...)
 |      x.__rtruediv__(y) <==> y/x
 |  
 |  __rxor__(...)
 |      x.__rxor__(y) <==> y^x
 |  
 |  __setattr__(...)
 |      x.__setattr__('name', value) <==> x.name = value
 |  
 |  __setitem__(...)
 |      x.__setitem__(i, y) <==> x[i]=y
 |  
 |  __setslice__(...)
 |      x.__setslice__(i, j, y) <==> x[i:j]=y
 |      
 |      Use  of negative indices is not supported.
 |  
 |  __str__(...)
 |      x.__str__() <==> str(x)
 |  
 |  __sub__(...)
 |      x.__sub__(y) <==> x-y
 |  
 |  __truediv__(...)
 |      x.__truediv__(y) <==> x/y
 |  
 |  __xor__(...)
 |      x.__xor__(y) <==> x^y
 |  
 |  next(...)
 |      x.next() -> the next value, or raise StopIteration
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
 |  __new__ = <built-in method __new__ of type object at 0x8140000>
 |      T.__new__(S, ...) -> a new object with type S, a subtype of T
```

This suggests there is a method called 'next'. I suppose this method must be inherited, because I did not see it in the documentation for Values. 

Okay, but then why am I not seeing the methods called 'ensure_value', 'read_file' and 'read_module' 
when I type help(opt) if opt is a Values and Values has these methods?

---

### Post by Can+~ on 2008-05-21
optparse produces an object which holds each option as an attribute:

[PHP]opt.symbol
opt.form[/PHP]

I don't think this is very healthy, but with dir you can see what objects an object holds:

[PHP]print dir(opts)[/PHP]

produces a (iterable) list of elements inside it:

[PHP]['__cmp__', '__doc__', '__init__', '__module__', '__repr__', '__str__', '_update', '_update_careful', '_update_loose', 'ensure_value', 'long', 'name', 'read_file', 'read_module'][/PHP]

If you need to see what something does inside a function, you can see the documentation (via help())

[PHP]print help(opts.ensure_value)

or as a string:

print opts.ensure_value.__doc__[/PHP]

The python documentation holds a huge section for optparse, check it out:
[http://docs.python.org/lib/module-optparse.html](http://docs.python.org/lib/module-optparse.html)

---

### Post by unutbu on 2008-05-21
Thank you LaRoza and Can+~. Your information was helpful though I'm still busting with questions.

```
sudo apt-get install python-doc
grep -r read_module  /usr/share/doc/python2.5/html
```

returns nothing. :confused:

---

### Post by unutbu on 2008-05-21
According to help(opt), opt has a method called next.
```
 |  next(...)
 |      x.next() -> the next value, or raise StopIteration

```

When I run
```
#!/usr/bin/env python
from optparse import OptionParser
import optparse
parser = OptionParser()
parser.add_option("--symbol", dest="symbol", help="ticker symbol, e.g. IBM")
parser.add_option("--form", dest="form", help="'10-K' is the default")
(opt, args) = parser.parse_args()
a=opt.next
```

I get
```
20:16:53 kids@play:~% fetch-10K.py --symbol BRK-A --form 13F-HR
Traceback (most recent call last):
  File "/home/kids/bin/fetch-10K.py", line 12, in <module>
    a=opt.next
AttributeError: Values instance has no attribute 'next'
```

What's going on? Why did help(opt) tell me opt had a method called next?

---

### Post by Can+~ on 2008-05-21
Well, if you really, really need to iterate over them, then you can use the __dict__ of the instance opt.

[PHP]for key,value in opt.__dict__.items():
	print key,":",value[/PHP]

I still think this is not the proper way to use the optparse though.

---

### Post by unutbu on 2008-05-21
Ahh.. Can+~, Thank you, thank you, thank you!

This is really just an experiment to help me explore the language. I basically understand how to use optparse the intended way. 

I used this short script as an example of the problems I'm having finding good documentation on all the methods / data structures provided by python objects.

I'm finding that reading /usr/lib/python2.5/optparse.py
is actually easier than understanding the output of help.

Another thing I'm finding out is that python's documentation is relatively poor compared to perl's. If a perl module is named XYZ, you just type `perldoc XYZ` and you get examples of code showing how to use each and every method the module provides. Perl is a less disciplined and wilder language, but it has a user-friendliness that python (at least so far) seems to lack.

Many thanks again for your help.

---

### Post by imdano on 2008-05-22
Usually the best way to find out what a module does with Python is to check the online documentation. [http://docs.python.org/lib/module-optparse.html](http://docs.python.org/lib/module-optparse.html)

---

### Post by geirha on 2008-05-22
There's also an alternative to optparse:

[http://docs.python.org/lib/module-getopt.html](http://docs.python.org/lib/module-getopt.html)

---

### Post by unutbu on 2008-05-22
I was a little surprised that 

```
print str(opt)
```

returned

```
{'symbol': 'C', 'form': 'yoga'}
```

opt is a Values instance. On what kinds of objects can str operate? Is there a way I could have know in advance that str can operate on Values?

---

### Post by geirha on 2008-05-22
str(opt) runs opt.__str__(), so it depends on the class whether and how it has implemented the __str__()-method.

---

### Post by unutbu on 2008-05-22
When I put 
```
a=opt.__str__
print a

```
in the script, I get
```
<bound method Values.__str__ of <Values at 0xb7d26d2c: {'symbol': 'C', 'form': 'yoga'}>>
```

I know it's not kosher to mess with private methods, but are there python commands I can use to extract "{'symbol': 'C', 'form': 'yoga'}" from opt.__str__?

I tried to find out how str() is defined (to see how str() does it), but couldn't find its definition in /usr/lib/python2.5. I suppose because it is hard-coded in the python binary?

```
private@ease:~% grep -r 'def str(' /usr/lib/python2.5/
/usr/lib/python2.5/site-packages/DistUpgrade/sourceslist.py:  def str(self):
/usr/lib/python2.5/site-packages/aptsources/sourceslist.py:  def str(self):
/usr/lib/python2.5/lib-tk/Canvas.py:    def str(self):
/usr/lib/python2.5/locale.py:def str(val):

```

---

### Post by geirha on 2008-05-22
> **unutbu said:**
> When I put 
```
a=opt.__str__
print a

```


__str__ is a method, you set a to point to that method, not its return value. Try
```
a= opt.__str__()
print a

```

---

### Post by unutbu on 2008-06-28
I know self has a __class__ variable, which I use below. Using only Python code (not documentation) how can I coax self into telling me that it has a variable called __class__?

```
#!/usr/bin/python

class ParentClass:
    def __init__(self):
        dirlist=dir(self)
        print dirlist
#         help(self)
        astr=self.__class__
        print "Init of ParentClass being run by %s"%astr

    def peekaboo(self):
        pass

class ChildClass(ParentClass):
    def iseeyou(self):
        pass

parent=ParentClass()
child=ChildClass()

```

Returns:
```
% test.py
['__doc__', '__init__', '__module__', 'peekaboo']
Init of ParentClass being run by __main__.ParentClass
['__doc__', '__init__', '__module__', 'iseeyou', 'peekaboo']
Init of ParentClass being run by __main__.ChildClass

```

I've tried using dir and help, but neither of them reveal that self has a __class__ variable.

---

### Post by geirha on 2008-06-28
All objects has a __class__ member even though dir doesn't show it. If you use new-style classes it will be listed by dir though. (You get new-style classes by inheriting object) [http://www.python.org/doc/newstyle/](http://www.python.org/doc/newstyle/)

---

