---
title: "How can I access the function of a function?"
date: 2010-07-29
forum: Programming Talk
---

### Post by xaegis on 2010-07-29
How can I access the function nested in a function from within a function?

I cant seem to make it launch.
I am attempting to call the function and have it call 2 child functions in a while loop.

it says I am getting an: "UnboundLocalError: Local Variable referenced before assignment." 


:(

---

### Post by Some Penguin on 2010-07-29
Perhaps you should mention what language you're programming in.

---

### Post by schauerlich on 2010-07-29
He's been around here lately, it's in python. I only sort of get what you're talking about, so, please post the code.

---

### Post by shadylookin on 2010-07-29
Every language that I know of that allows inner functions doesn't allow other functions to call them. Consider structuring it as a class or to have it return a closure.

edit: or just break it into 2 functions.

---

### Post by lisati on 2010-07-29
When I was learning programming, many years ago, it was usual to think of functions and subroutines as a kind of "black box". What mattered most was that you called the function/subroutine correctly and that the results it returned were what you needed in your program. It didn't really matter how it went about its business, and you normally only accessed its "internal workings" if you were maintaining the underlying code or writing a new version that suited your needs better.

---

### Post by splicerr on 2010-07-29
I think you mean something like this:

```

def foo():
    def bar():
        print 'hello'
    bar()

foo()

```

---

### Post by xaegis on 2010-07-30
Sorry I forgot to mention that it is in fact python.

:)

I dont want to post the code because it is so incredibly messy and non pep8!!!
:(

it looks like this:

```


def function1():
    print (stuff)

        def function2():
            print (stuff)

        def function3():
            print(more stuff)


```
How can I get at the inner functions, function2 and function3? I'm assuming they both inherit variables from function1 which is why I did it that way.

Thanks everyone!

---

### Post by CptPicard on 2010-07-30
The function object in Python is not the same kind of namespace dictionary as a module is, so the inner functions are not present in "dir(function1)". I guess you could try accessing the __code__ attribute for the function's code object, you may be able to get some kind of a handle through that. However, I guess you're thinking about this wrong... the inner functions alone are not particularly meaningful as they always exist within the context of some particular outer function invocation. Not sure how an inner function would be defined if you could get to it from the outside.

---

### Post by Åtta on 2010-07-30
> **xaegis said:**
> How can I get at the inner functions, function2 and function3? I'm assuming they both inherit variables from function1 which is why I did it that way.
It seems to me like you would probably benefit from something like this:
```
class FancyMethods:
	def __init__(self):
		self.x = "our common variable"
		print "Initialized " + self.x
		
	def method1(self):
		print "Method 1 is using " + self.x
		
	def method2(self):
		print "But method 2 should also be able to access " + self.x 

if __name__ == '__main__':
	Instance = FancyMethods()
	Instance.method1()
	Instance.method2()
```

---

### Post by StephenF on 2010-07-30
The inner functions are not defined until the def just as the outer functions are not defined until the module execution point has reached a particular function definition. That means the inner functions are effectively remade each time the outer is called and unmade whenever the function exits since it is defined locally. The exception is when the inner function is passed out as a return value but this does not mean the inner function persists inside the outer. Functions have an existence all of their own but are subject to Pythons scoping rules.

To illustrate why trying to call an inner function within an outer directly is impossible I offer the following. As you can see to decide which form of the inner function you would get would require code execution in the outer function which implies you have to call the outer function.
```

import random
def foo():
    #bar() # Try uncommenting this.
    if random.randint(0, 1) == 0:
        def bar():
            print "0"
    else:
        def bar():
            print "1"

    bar()

for x in xrange(100):
    foo()

```
When using threads to call the same function you could end up with a situation where the two different forms of bar exist concurrently.

This example demonstrates how the inner function can be used to trap local variables of foo when exported.
```

import random
def foo(val):
    if random.randint(0, 1) == 0:
        def bar():
            print val, "0"
    else:
        def bar():
            print val, "1"

    return bar

for x in xrange(100):
    inner = foo(x)
    inner()

```
Perhaps the code you were reaching for was...
```

class Namespace(object):
    @staticmethod
    def f1():
        print "f1 called"
    @staticmethod
    def f2():
        print "f2 called"
        
Namespace.f1()
Namespace.f2()

```
You can use something like this to pass a suite of functions to wherever it needs to go where you might want two different implementations with the same interface but do not want to write them in separate modules.

---

### Post by xaegis on 2010-07-30
> **StephenF said:**
> The inner functions are not defined until the def just as the outer functions are not defined until the module execution point has reached a particular function definition. That means the inner functions are effectively remade each time the outer is called and unmade whenever the function exits since it is defined locally. The exception is when the inner function is passed out as a return value but this does not mean the inner function persists inside the outer. Functions have an existence all of their own but are subject to Pythons scoping rules.

To illustrate why trying to call an inner function within an outer directly is impossible I offer the following. As you can see to decide which form of the inner function you would get would require code execution in the outer function which implies you have to call the outer function.
```

import random
def foo():
    #bar() # Try uncommenting this.
    if random.randint(0, 1) == 0:
        def bar():
            print "0"
    else:
        def bar():
            print "1"

    bar()

for x in xrange(100):
    foo()

```
When using threads to call the same function you could end up with a situation where the two different forms of bar exist concurrently.

This example demonstrates how the inner function can be used to trap local variables of foo when exported.
```

import random
def foo(val):
    if random.randint(0, 1) == 0:
        def bar():
            print val, "0"
    else:
        def bar():
            print val, "1"

    return bar

for x in xrange(100):
    inner = foo(x)
    inner()

```
Perhaps the code you were reaching for was...
```

class Namespace(object):
    @staticmethod
    def f1():
        print "f1 called"
    @staticmethod
    def f2():
        print "f2 called"
        
Namespace.f1()
Namespace.f2()

```
You can use something like this to pass a suite of functions to wherever it needs to go where you might want two different implementations with the same interface but do not want to write them in separate modules.

I was trying to do it with functions and not methods but maybe I'll try that when I get internet access again in a week. Thank you everyone for all the advice and stimulating conversation! :D

---

### Post by StephenF on 2010-07-30
> **xaegis said:**
> I was trying to do it with functions and not methods
```

>>> class Namespace(object):
...     @staticmethod
...     def f():
...         pass
... 
>>> 
>>> type(Namespace.f)
<type 'function'>

```
Python says it's a function.

---

