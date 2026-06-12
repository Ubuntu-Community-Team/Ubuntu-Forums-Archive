---
title: "Python: Is there official static initializer?"
date: 2010-08-10
forum: Programming Talk
---

### Post by jw37 on 2010-08-10
Hi all!

I'd like to create a class with a static constructor/initializer. It means a method that is automatically run when the class is accessed the first time. I haven't found it by reading tutorials but that doesn't necessarily mean that it wouldn't exist (in Visual Basic, which I used to use, I found it by trying, but that was not mentioned in the documentation!).

You can do some trick to achieve the same functionality, but it would be way much cooler to use the official method you know. If there is one.

In case there isn't the official method, what is your simpliest solution to the problem?

Thanks in advance for your answers.

---

### Post by Reiger on 2010-08-10
Two ways that my limited experience with Python might tempt me with: 

One & ugly: first time a object is created have the __init__ method double as static initializer, and set a state flag after itself in your module.

Second:
Do without the static initializer for a class: use the module instead. Requires a change of mindset, rather more modules but it does look more proper to me.

---

### Post by jw37 on 2010-08-10
I seriously consider the module issue. That's quite a nice idea :-]  The first one isn't so bad at all, too.

Any other ideas/experiences, folks?

(In C++ you have to do things like that:
[http://stackoverflow.com/questions/1197106/static-constructors-in-c-need-to-initialize-private-static-objects](http://stackoverflow.com/questions/1197106/static-constructors-in-c-need-to-initialize-private-static-objects)
Not very nice...)

---

### Post by StephenF on 2010-08-11
While playing around a while back I wrote this
```

import time

def lazyinit(method):
    def inner(cls):
        def call(*args, **kwds):
            if not hasattr(cls, "instance"):
	        cls.instance = cls()
	    return getattr(cls.instance, method)(*args, **kwds)
	return call
    return inner

@lazyinit("worker")
class foo(object):
    def worker(self):
        print "foo do work"

    def __init__(self):
        print "foo initialization"
	# Simulate expensive initialization
        time.sleep(2)

@lazyinit("worker")
class bar(object):
    def worker(self):
        print "bar do work"

    def __init__(self):
        print "bar initialization"
	time.sleep(2)

# Test code.
foo()
foo()
bar()
bar()
foo()
bar()
foo()
bar()

```
The idea was to implement a single function with one time initializer code. As a basis for a class it implements the singleton pattern but does not support subclassing.

You could adapt this so the "worker" returns the instance (self in other words) and add another method, baz, and access it like this.

foo().baz()

Python does not try to formalize design patterns within the language as to do so would cause it to become a big ugly mess. Instead it offers the tools to allow you to create your own for example metaclasses, function decorators, special methods for controlling attribute access.

---

### Post by surfer on 2010-08-11
```

#!/usr/bin/python


def once(theClass):
	print 'hello from once(theClass)'
	return theClass

@once
class TheClass(object):

	def __init__(self):
		print '%s initialized' % id(self)

if __name__ == '__main__':

	a = TheClass()
	b = TheClass()


```

is about the same idea as the post above - using decorators.

i usually use something like this to create a sigleton pattern,

---

### Post by surfer on 2010-08-11
```

#!/usr/bin/python


def once():
	print 'hello from once()'


class TheClass(object):

	once()

	def __init__(self):
		print '%s initialized' % id(self)

if __name__ == '__main__':

	a = TheClass()
	b = TheClass()

```

that is also a pretty simple way to do it.

---

### Post by jw37 on 2010-08-11
StephenF: To be honest, I didn't understand your code & explanation very well because I'm so beginner. Thanks anyway :]

I didn't even know that you can use decorators with classes (not only functions).

surfer: That's very simple indeed :]  I like it. I would have never imagined that the initializer method (function) could be outside the class definition! Well now that I think about it, Reiger's idea to use module is quite the same but without that separate function.

It's practical that there are not really private class members ;)

I thank you all. I believe these are good means for my purposes. But of course discussion can be continued in case someone wants to comment or present another way to create a 'static initializer'. :]

---

### Post by jw37 on 2010-08-11
OMG, you know what I just realized... That you don't need a function/method for static/class initialization because you can simply write the code in the beginning of the class! :D  (as in surfer's example the function call once())

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

class Gadget(object):
    # class initialization code
    _var = 123
    # ... other statements, don't have to be just assignments ...
    print "Class Gadget is now initialized."
    
    def __init__(self):
        print repr(self), "is now initialized."


a = Gadget()
b = Gadget()
```


I was stuck in other languages' syntax where executable code must be inside a function. What a noise about so simple thing! Sorry guys :-[  However you helped me a lot, thanks once more! :-]

---

### Post by surfer on 2010-08-11
yes, you can write just about anything in the class definition. there is just no way to call a function you have defined inside that class (as the class is not yet defined at that point).

...python is sooo beautiful!

---

