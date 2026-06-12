---
title: "Static Attributes in Python"
date: 2009-07-23
forum: Programming Talk
---

### Post by SunSpyda on 2009-07-23
Can anyone tell me a way to make static attributes, that doesn't involve a ugly hack job to get it working? Global doesn't cut it - they need to remain private to the class. It seems like such a chore, considering I started learning Python to make my life easier :D

I thought *I can use global privates to do the same thing*, but I soon found this didn't work - the class can read them fine, but when I try to write to them, it doesn't work.

So, why can't Python use real static attributes, like in C++ or Java?

---

### Post by monraaf on 2009-07-23
You mean like?

[PHP]
class foo(object):
    bar = 0
[/PHP]

---

### Post by SunSpyda on 2009-07-23
That isn't static. I know how to make instance variables like that, but I don't know how to make statics.

---

### Post by monraaf on 2009-07-23
Obviously you don't know.

---

### Post by JordyD on 2009-07-23
Googling gave me this:
[http://www.daniweb.com/forums/thread33025.html]("http://www.daniweb.com/forums/thread33025.html")

Help?

---

### Post by Can+~ on 2009-07-23
[PHP]#!/usr/bin/env python

class Sample(object):
	
	x = 10
	
	def __init__(self):
		self.y = 5

# Instances
samp1 = Sample()
samp2 = Sample()

print "Init:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x

# Modify the class
Sample.x = 9

# See what happend on the instances
print
print "Sample.x = 9:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x

# Modify one of the childs
samp1.x = 666

# See what happend on the instances and class
print
print "samp1.x = 666:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x
[/PHP]

Children of the class can see what's on their parent (Sample.x) unless it's override (samp1.x = ???).

---

### Post by smartbei on 2009-07-24
If you want static methods, there is the @staticmethod decorator...
```

class C(object):
    @staticmethod
    def my_static_method(arg1, arg2):
        """ Note there is no self """
        ...

```
And my_static_method will behave just like you would expect. staticmethod is a built-in, so you don't need to do anything to import it.

---

### Post by SunSpyda on 2009-07-26
> **monraaf said:**
> You mean like?

[PHP]
class foo(object):
    bar = 0
[/PHP]

> **monraaf said:**
> Obviously you don't know.

Yeah, you're right, I didn't know, I got confused with the syntax.

I thought that bar was non-static, as different instances of the class had different values. But if I referred to that through the class name, over the instance name, it acted as a static. Is that right?

Thanks for pointing that out. And thanks everyone else for elaborating.

---

### Post by CHW on 2010-02-18
> **Can+~ said:**
> [PHP]#!/usr/bin/env python

class Sample(object):
	
	x = 10
	
	def __init__(self):
		self.y = 5

# Instances
samp1 = Sample()
samp2 = Sample()

print "Init:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x

# Modify the class
Sample.x = 9

# See what happend on the instances
print
print "Sample.x = 9:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x

# Modify one of the childs
samp1.x = 666

# See what happend on the instances and class
print
print "samp1.x = 666:"
print " class:", Sample.x, "  1:", samp1.x, "  2:", samp2.x
[/PHP]

Children of the class can see what's on their parent (Sample.x) unless it's override (samp1.x = ???).

> **smartbei said:**
> If you want static methods, there is the @staticmethod decorator...
```

class C(object):
    @staticmethod
    def my_static_method(arg1, arg2):
        """ Note there is no self """
        ...

```
And my_static_method will behave just like you would expect. staticmethod is a built-in, so you don't need to do anything to import it.

Thank you Can+~ and smartbei, being new to Python I found an elegant way to solve my problem because of your answers!

I wanted to design a class with static proprieties as your methods suggest, but with private variables.

The reason why I needed static proprieties is that my objects depend on a state which can change occasionally, but I wanted to create a lot of instances with the same state without always passing those state variables to the __init__ function. This would be very inefficient in my case, because the input is further computed and tested, which is an expensive operation. So I create instance copies of these static variables.

So after a long search I found this code.
[PHP]class Foo:
  __x
  def __init__(self):
    self.__localcopy_x = self.__x
    # now the global state can change without affecting the local copy

  def someMethod(self):
    # use self.__localcopy_x to compute

  @staticmethod
  def setAttributes(a):
    # some expensive computations on a
    Foo.__x = a

if __name__ == "__main__":
  Foo.setAttributes(5)
  var = Foo()
  var.someMethod()
  # create more instances of Foo...
  Foo.setAttributes(10)
  # create instances of Foo wih the new attributes[/PHP]
I hope that this helps someone in future :D

---

### Post by nvteighen on 2010-02-18
> **CHW said:**
> Thank you Can+~ and smartbei, being new to Python I found an elegant way to solve my problem because of your answers!

I wanted to design a class with static proprieties as your methods suggest, but with private variables.

The reason why I needed static proprieties is that my objects depend on a state which can change occasionally, but I wanted to create a lot of instances with the same state without always passing those state variables to the __init__ function. This would be very inefficient in my case, because the input is further computed and tested, which is an expensive operation. So I create instance copies of these static variables.

So after a long search I found this code.
[PHP]class Foo:
  __x
  def __init__(self):
    self.__localcopy_x = self.__x
    # now the global state can change without affecting the local copy

  def someMethod(self):
    # use self.__localcopy_x to compute

  @staticmethod
  def setAttributes(a):
    # some expensive computations on a
    Foo.__x = a

if __name__ == "__main__":
  Foo.setAttributes(5)
  var = Foo()
  var.someMethod()
  # create more instances of Foo...
  Foo.setAttributes(10)
  # create instances of Foo wih the new attributes[/PHP]
I hope that this helps someone in future :D

Hm... that won't work in all cases. If Foo.__x is what Python calls a "mutable object" (lists, dictionaries and custom classes), then, self.__localcopy_x won't be a copy, but a reference/pointer to that object which if modified, it will also modify the original.

If you want to be 100% sure that you're copying stuff, use the copy module's deepcopy() function.

---

### Post by CHW on 2010-02-18
> **nvteighen said:**
> Hm... that won't work in all cases. If Foo.__x is what Python calls a "mutable object" (lists, dictionaries and custom classes), then, self.__localcopy_x won't be a copy, but a reference/pointer to that object which if modified, it will also modify the original.

If you want to be 100% sure that you're copying stuff, use the copy module's deepcopy() function.

Ok, thank you very much for this hint!
You probably saved me a lot of debugging time! ;)

I have implemented deepcopy() now, but I still have to implement some test suites to get valuable test results, so I didn't notice this problem before. 

I'm quite new to python, so just to be sure if I have understood correctly the concept of what is mutable:
[LIST]
[*]a tuple for example is immutable
[*]and a list is mutable?
[/LIST]

So if I have a mutable object, should I always use deepcopy() if I don't want to create a reference?

---

### Post by nvteighen on 2010-02-18
> **CHW said:**
> Ok, thank you very much for this hint!
You probably saved me a lot of debugging time! ;)

I have implemented deepcopy() now, but I still have to implement some test suites to get valuable test results, so I didn't notice this problem before. 

I'm quite new to python, so just to be sure if I have understood correctly the concept of what is mutable:
[LIST]
[*]a tuple for example is immutable
[*]and a list is mutable?
[/LIST]

So if I have a mutable object, should I always use deepcopy() if I don't want to create a reference?

Why did you reimplement deepcopy()? Just do **import copy** and use **copy.deepcopy(object)**! (There's a "swallow" copy function, copy.copy()... but it may be even more difficult to use correctly; look at Python's docs).

Yes, a tuple is immutable; the list is its mutable counterpart.

Actually, the need for a copy is rather smaller than it might seem to you at first sight. Using references for mutable objects makes life easier in many cases... my Python programs usually play with this idea a lot... :p

---

### Post by CHW on 2010-02-18
Oh, I expressed myself not very clearly, of course I imported the copy module and didn't reinvent the wheel ;)

I guess I have to think a little bit more about references in Python...
Coming from C++ this automatism is a little bit unusual for me, but every Day I get more familiar with Python :)

---

