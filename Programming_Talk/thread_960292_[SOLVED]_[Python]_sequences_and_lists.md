---
title: "[SOLVED] [Python] sequences and lists"
date: 2008-10-27
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-27
I am really not a professional with python. When creating a class, there can be passed a parent argument, like this:
```
class MyClass(object):
```
If I want to create an object type which I can handle like a list, how do I do it?
I would like it to be like a normal list/sequence but while having some functions and stuff.
Like this:
```
>>>a = MyClass([1, 2, 3])
>>>print a
[1, 2, 3]
>>>a.pop(0)
>>>print a
[2, 3]
>>>a.append(16)
>>>for x in a: print x
2
3
16
>>>a.extrafunc()
```
I know this is possible but can't find anything with google.

---

### Post by y-lee on 2008-10-27
Several ways to do that, but one of the simplest is:

```
class MyClass(list):
    
    def extrafunc(self):
        # whatever
        return sum(self)
```

---

### Post by geirha on 2008-10-27
class MyClass(object): will make the class inherit from the object class, it does not set the arguments for the constructor (__init__). Try inheriting from the list class.

An simple example:
```

class MyClass(list):
    def __init__(self, sequence):
        list.__init__(self, sequence)
    def extrafunc(self):
        return self+self

```

---

### Post by crazyfuturamanoob on 2008-10-27
What if I want to create the list's content in it's __init__ function?
Will it be like "self = value"?

---

### Post by geirha on 2008-10-27
Almost.

```

>>> class MyClass(list):
...     def __init__(self, sequence):
...         list.__init__(self, sequence)
...         self.foo= 5
...     def extrafunc(self):
...         return self+self
... 
>>> a=MyClass([1,2,3])
>>> print a
[1, 2, 3]
>>> print a.foo
5

```

---

### Post by crazyfuturamanoob on 2008-10-27
Solved. BTW that was my 50th thanks given :D

---

### Post by pmasiar on 2008-10-27
> **crazyfuturamanoob said:**
> When creating a class, there can be passed a parent argument, like this:
```
class MyClass(object):
```

Wrong. When defining class, you pass it parent **class** (to inherit from) not object.

---

### Post by geirha on 2008-10-27
> **pmasiar said:**
> Wrong. When defining class, you pass it parent **class** (to inherit from) not object.

Yes, and object is a class ...

---

### Post by pmasiar on 2008-10-27
> **geirha said:**
> Yes, and object is a class ...

Not at all. Object is **instance** of a class, not the class. Don't confuse children ;-)

Class is cookie cutter, instance (object) is a cookie. You won't eat the cutter, would you?

When defining class, you provide parent class(es) to inherit from, not the instances. You cannot inherit code from the instance, it has no own code (only data): code is in class. This difference is so fundamental. I lost any confidence in your advice, geirha. Really.

I guess this is result from learning Java or C++ without understanding C and ASM:  OOP becomes "magic sauce" without any reference to reality, how it is implemented. OO was just a "design pattern" in C before it became part of syntax of OOP languages.

---

### Post by crazyfuturamanoob on 2008-10-27
But if I give "object" as a parent for a class, it doesn't make errors. So "object" must be another class.

---

### Post by gomputor on 2008-10-27
> **geirha said:**
> Yes, and object is a class ...
If you are referring to ```
class MyClass(object):
``` you are right (anyway you are right).

> **crazyfuturamanoob said:**
> But if I give "object" as a parent for a class, it doesn't make errors. So "object" must be another class.
Yes, "**object**" is a class. You can say that "**object**" is a superclass or the baseclass. Everything is an object
and every object is an instance of a class. All classes inherit from "**object**" and all objects are instances
of "**object**".
Note that this is the new-style classes (after Python 2.2.) After Python 3.0 they will be the only
classes to exist, old-style classes will be gone. So you can stick to the new-style classes.

---

### Post by nvteighen on 2008-10-27
> **pmasiar said:**
> 
Class is cookie cutter, instance (object) is a cookie. You won't eat the cutter, would you?

Fabulous example!!

> I guess this is result from learning Java or C++ without understanding C and ASM:  OOP becomes "magic sauce" without any reference to reality, how it is implemented. OO was just a "design pattern" in C before it became part of syntax of OOP languages.

Very possible, indeed. Understanding that OO is (still) done in C by creating a data structure and then defining relevant functions that accept some instance of that data structure as an argument quickly destroys that sort of "magical thinking" around OOP languages.

OOP languages implement some ways to have OOP easier by supporting useful techniques like inheritance just at hand. Inheritance in C is not trivial, but possible... if you don't believe me, please learn how GTK+ works in C.

---

### Post by pp. on 2008-10-27
> **crazyfuturamanoob said:**
> there can be passed a parent argument, like this:
```
class MyClass(object):
```

> **pmasiar said:**
> Wrong. When defining class, you pass it parent **class** (to inherit from) not object.

crazy&c is right because the wording of the post ('like this') implies that the letter sequence 'object' is to be taken as actual parameter. 'object' is indeed the identifier of a class and therefore is a legal value for the argument of the class declaration.

pmasiar would be right if the letter sequence 'object' was meant to be a formal parameter and and the name 'object' was used to indicate that an instance of class object was to be used as actual parameter.

---

