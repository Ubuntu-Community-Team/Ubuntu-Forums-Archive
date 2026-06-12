---
title: "Best Python Style - providing a wrapper class"
date: 2009-08-21
forum: Programming Talk
---

### Post by Tony Flury on 2009-08-21
Is there a generic python way of creating a simple super class that will extend every method in the base class, without needing to explicitly superseed every base class method.

In nearly all cases the extension will be exactly the same functionality added around the call to the base class method - and the exceptions are trivial.

What i think i need is to define a method on my super class, which is a catch all (i.e. is called when any method is invoked) and then implement my own functionality around the call to the specific Base class method.

clearly this catch all method would need to be able to handle variable arguments, and i would need to be able to use a string (i assume) to call a Base class method.

Is all of this possible ?

---

### Post by smartbei on 2009-08-21
Sure this is possible - through the use of the getattr slot (__getattr__):
```

class Wrapper(object):
	def __init__(self, obj):
		self.obj = obj
		
	def __getattr__(self, name):
		func = getattr(self.__dict__['obj'], name)
		if callable(func):
			def my_wrapper(*args, **kwargs):
				print "entering"
				ret = func(*args, **kwargs)
				print "exiting"
				return ret
			return my_wrapper
		else:
			return func

```
As you can see, we return our own function whenever the user calls one of the original functions. (this is very similar to decorators)
To use:
```

## for example on a string:
s = 'abc'
w = Wrapper(s)
print w.isdigit()

```

If you want to change what happens on every call, simply change the my_wrapper function.

EDIT:
Note also the *args, **kwargs that my_wrapper receives as arguments. This is how you do variable argument passing in python. args is a tuple that catches all of the normal, non-keyword arguments, and kwargs is a dictionary between each keyword and its value.

---

### Post by delfick on 2009-08-21
Another way is to design your classes such that you extend only a part of the function.

So for example, we have an object where we must called object.execute() which involves printing some generic message, some processing, followed by another generic message.

And depending on the current state of the program, different processing is required.

we could do something like

[php]
class defaultExecutor(object):
    def execute(self, *args, **kwargs):
        print "hello there"
        self.process(*args, **kwargs)
        print "done stuff"

    def process(self, *args, **kwargs):
        """this becomes the method to be overridden"""
        x = 1
        x += 1
        print x

class OtherExecutor(defaultExecutor):
    def process(self, *args, **kwargs):
        return 3
[/php]

To make life nice you'd design it so that process has some specific set of arguements instead of using * and ** magic (unless of course that would be appropiate)

I tend to do this when I have classes that all need to do the same thing in __init__ but still might require something different in each case, so I don't have to overwrite __init__ and do super calls and such.


Also, another way is to use function decorators.

for example

[php]
def decorator(func):
    def wrapped(*args, **kwargs):
        print "hello there"
        func(*args, **kwargs)
        print "done stuff"
    return wrapped

class otherExecutor(object):
    @decorator
    def execute(self, *args, **kwargs):
        return 3
[/php]

:)

---

### Post by Tony Flury on 2009-08-21
thank you both ...

Most helpful.

---

