---
title: "Python Namespace and Private Functions"
date: 2008-10-27
forum: Programming Talk
---

### Post by Aikon- on 2008-10-27
Hi everyone,

I'm having a bit of an issue working on a Python module for school.. Basically, I have a module called `fobjects.py' which mainly contains class definitions for various finite element objects. I am trying to add a utility function to the module that would greatly reduce the amount of code I need to repeat but that doesn't belong in any of the classes themselves:

```
class Node(object):
    def __init__(self):
        pass

class Stiffness(object):
    def __init__(self, nodes):
        pass
    def remove_dof(self, i, in_place=False):
        self.K = remove_ij(self.K,i,i,in_place)
        return self

def remove_ij(x, i, j, in_place=False):
    pass
```

This works fine (I've omitted basically all the code; I'm just talking structure here). Now, the problem is that I don't really want this utility function `remove_ij' to be visible outside of this module; it's only use is for the classes defined here. So, I tried to make it private:

```
class Node(object):
    def __init__(self):
        pass

class Stiffness(object):
    def __init__(self, nodes):
        pass
    def remove_dof(self, i, in_place=False):
        self.K = __remove_ij(self.K,i,i,in_place)
        return self

def __remove_ij(x, i, j, in_place=False):
    pass
```
    
which gives me the error

```
Traceback (most recent call last):
  File "fem.py", line 153, in <module>
    print Kg.remove_dof(3)
  File "fobjects.py", line 97
    self.K = __remove_ij(self.K,i,i,in_place)
NameError: global name '_Stiffness__remove_ij' is not defined
```

Some help on this would be greatly appreciated; I've been doing some simple Python programming for a while, but this is my first actual ``application'', so I'm new to the whole modules and namespace issues.

Cheers,
-Aikon

---

### Post by pmasiar on 2008-10-27
> **Aikon- said:**
>  working on a Python module for school.. 

Great, so there **are** smart schools where people recognize Python is OK as first language? Or did you suffered through another language before?

For plain private function use single underscore prefix: _remove_ij. Double underscore is for reserved methods, "name mangling" and other esoteric stuff.

---

### Post by Aikon- on 2008-10-27
> **pmasiar said:**
> Great, so there **are** smart schools where people recognize Python is OK as first language? Or did you suffered through another language before?

For plain private function use single underscore prefix: _remove_ij. Double underscore is for reserved methods, "name mangling" and other esoteric stuff.

Well, in high school I did C and a hint of Java; in first-year university I did C and C++; at my summer job two years in a row I did Java (with JSPs); since then I've been using mostly MATLAB.

I'm actually a grad student in Aerospace Engineering, so the code isn't technically for this course.. the course is on multi-disciplinary optimization, and I've chosen to write mine in Python. Having said that though, my instructor (Dr. J.R.R.A. Martins, [http://mdolab.utias.utoronto.ca/](http://mdolab.utias.utoronto.ca/)) is pretty big on Python, and they've got a pretty intense MDO library written in Python.

== On Topic ==

So, the double-preceeding underscore is only for private methods (i.e. part of a class) and not private functions (part of a module)? I was going based on this bit of styleguid:

> In addition, the following special forms using leading or trailing underscores are recognized (these can gerally be combined with any case convention):

    * _single_leading_underscore: weak "internal use" indicator (e.g. "from M import *" does not import objects whose name starts with an underscore).
    * single_trailing_underscore_: used by convention to avoid conflicts with Python keyword, e.g. Tkinter.Toplevel(master, class_="ClassName").
    * __double_leading_underscore: class-private names in Python 1.4.
    * __double_leading_and_trailing_underscore__: "magic" objects or attributes that live in user-controlled namespaces, e.g. __init__, __import__ or __file__. Sometimes these are defined by the user to trigger certain magic behavior (e.g. operator overloading); sometimes these are inserted by the infrastructure for its own use or for debugging purposes. Since the infrastructure (loosely defined as the Python interpreter and the standard library) may decide to grow its list of magic attributes in future versions, user code should generally refrain from using this convention for its own use. User code that aspires to become part of the infrastructure could combine this with a short prefix inside the underscores, e.g. __bobo_magic_attr__.

---

### Post by Aikon- on 2008-10-27
p.s. I think I may have mislead a bit.. I've only ever done basic apps in Python; in other languages (particular MATLAB) I've done a fair bit of complex stuff (mostly involving finite element modelling and computational fluid dynamics, so a lot of vector/matrix math and large data-sets).

Also I did a 1-year internship at a financial modelling company doing database programming in T-SQL (blech), which is where I fell in love with scripting (using Python, PHP, and VBS) to automate my daily maintenance stuff =)

Aikon-

---

### Post by pmasiar on 2008-10-27
> __double_leading_underscore: class-private names in Python 1.4.

[http://www.python.org/doc/1.5/tut/node67.html](http://www.python.org/doc/1.5/tut/node67.html)

"Any identifier of the form __spam (at least two leading underscores, at most one trailing underscore) is now textually replaced with _classname__spam, where classname is the current class name with leading underscore(s) stripped"

More current: [http://www.python.org/doc/2.5.2/ref/atom-identifiers.html](http://www.python.org/doc/2.5.2/ref/atom-identifiers.html)

Just use simple underscore as prefix and don't dive too deep into OOP magic just yet.

---

### Post by Aikon- on 2008-10-27
Ah, OK.. makes sense now that I've read the relevant documentation. Finding said documentation isn't always easy though =P

Thanks a bunch =)

---

