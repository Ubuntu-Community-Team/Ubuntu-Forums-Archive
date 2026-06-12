---
title: "functions in python"
date: 2006-03-07
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-07
I have the following code

```

class test:
    def __init__(self):
        print 'This is init'        
    def action(self):
        print 'this is action'
        do_nothing(self)
        do_something(self)
    def do_something(self):
        print 'Do something'
    def do_nothing(self):
        print 'Do Nothing'

t = test()
t.action()

```

I get the following error, can you please tell me whats going wrong out here.

```

Traceback (most recent call last):
  File "func_check.py", line 17, in ?
    t.action()
  File "func_check.py", line 8, in action
    do_nothing(self)
NameError: global name 'do_nothing' is not defined

```

Thanks

---

### Post by gord on 2006-03-07
```

class test:
    def __init__(self):
        print 'This is init'        
    def action(self):
        print 'this is action'
        self.do_nothing()
        self.do_something()
    def do_something(self):
        print 'Do something'
    def do_nothing(self):
        print 'Do Nothing'

t = test()
t.action()

```

that should work :) 

you need to add self.<function> when you are accesing an objects function from inside the object. and you don't pass self to the functions, python automatically does that.

---

### Post by krypto_wizard on 2006-03-07
Worked like a charm!!! Thanks so much..I spend an hour without realizing this trivial mistake which you pointed out.

---

### Post by thumper on 2006-03-07
Dude - you're still using old style classes.

Move on...

```
class test(object):
```

Many new techniques don't work with old style classes, but do with the new ones.  So get into the habit for all classes you write to be new ones :)

---

### Post by dabear on 2006-03-07
Please explain the difference between new and old style classes? Is the only difference that they inherit from "object"?

---

### Post by krypto_wizard on 2006-03-07
Oh yes I realized that.I should be more particular in using new style classes. Thanks Thumper.

[QUOTE=thumper]Dude - you're still using old style classes.

Move on...

```
class test(object):
```

Many new techniques don't work with old style classes, but do with the new ones.  So get into the habit for all classes you write to be new ones :)[/QUOTE]

---

### Post by thumper on 2006-03-07
[QUOTE=dabear]Please explain the difference between new and old style classes? Is the only difference that they inherit from "object"?[/QUOTE]
New style objects were introduced in python 2.2.  A class is new-style if it inherits either directly or indirectly from the built-in type object.

As well as adding a few new method, new style classes also add type types of class level methods that are not available in "classic" classes: static methods and class methods.

Here's the code from "Python in a Nutshell" w.r.t these methods.

A static method has no self reference.
```
class AClass(object):
   def astatic(): print 'a static method'
   astatic = staticmethod(astatic)
anInstance = AClass()
AClass.astatic()  # prints: a static method
anInstance.astatic()  # prints: a static method

```
A class method gets the class object passed as a parameter.
```
class ABase(object):
   def aclassmet(cls): print 'a class method for', cls.__name__
   aclassmet = classmethod(aclassmet)
class ADeriv(ABase): pass
bInstance  = ABase()
dInstance = ADeriv()
ABase.aclassmet()     # prints: a class method for ABase
bInstance.aclassmet()  # prints: a class method for ABase
ADeriv.aclassmet()    # prints: a class method for ADeriv
dInsatnce.aclassmet()  # prints: a class method for ADeriv

```
The new additions also allow interesting things to happen with metaclasses.

Metaclasses are interesting and powerful, and a bit beyond me at the moment.

---

### Post by krypto_wizard on 2006-03-07
Thanks for the info thumper, what the best resource(web or book) to update about the latest and good habits in python.

[QUOTE=thumper]New style objects were introduced in python 2.2.  A class is new-style if it inherits either directly or indirectly from the built-in type object.

As well as adding a few new method, new style classes also add type types of class level methods that are not available in "classic" classes: static methods and class methods.

Here's the code from "Python in a Nutshell" w.r.t these methods.

A static method has no self reference.
```
class AClass(object):
   def astatic(): print 'a static method'
   astatic = staticmethod(astatic)
anInstance = AClass()
AClass.astatic()  # prints: a static method
anInstance.astatic()  # prints: a static method

```
A class method gets the class object passed as a parameter.
```
class ABase(object):
   def aclassmet(cls): print 'a class method for', cls.__name__
   aclassmet = classmethod(aclassmet)
class ADeriv(ABase): pass
bInstance  = ABase()
dInstance = ADeriv()
ABase.aclassmet()     # prints: a class method for ABase
bInstance.aclassmet()  # prints: a class method for ABase
ADeriv.aclassmet()    # prints: a class method for ADeriv
dInsatnce.aclassmet()  # prints: a class method for ADeriv

```
The new additions also allow interesting things to happen with metaclasses.

Metaclasses are interesting and powerful, and a bit beyond me at the moment.[/QUOTE]

---

### Post by WelterPelter on 2006-03-07
I would recommend the Google group comp.lang.python 
It's a user group with a passle of real python gurus in it. All the guys who write the books are there. [http://groups.google.com/group/comp.lang.python?lnk=li]("http://groups.google.com/group/comp.lang.python?lnk=li")

As far as books are concerned, try [Python in a Nutshell]("http://www.amazon.com/gp/product/0596001886/sr=8-5/qid=1141752062/ref=pd_bbs_5/102-1227090-0902524?%5Fencoding=UTF8"), by Alex Martinelli. Great book.

---

### Post by thumper on 2006-03-07
I haven't found any books that are entirely up to date.  Python in a Nutshell is very good though.

I tend to read the [python website](http://www.python.org) reasonably often to see what has changed.

Python Cookbook, 2nd Ed by Martelli, Ravenscroft and Ascher is very good for covering idiomatic programming that you don't normally get in other books.

---

