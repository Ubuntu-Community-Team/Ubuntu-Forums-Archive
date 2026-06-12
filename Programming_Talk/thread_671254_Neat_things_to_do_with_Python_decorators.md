---
title: "Neat things to do with Python decorators"
date: 2008-01-18
forum: Programming Talk
---

### Post by Wybiral on 2008-01-18
I've been reading quite a bit of Python code lately and I've noticed that a lot of Python programmers rarely make use of decorators (even when they make sense to use). They're a really nifty feature in Python and I personally feel like they're being under appreciated! I want this thread to be a place where people can post interesting uses for decorators that they've come across. I'll start with a few of my favorite (albeit, obvious) uses for decorators. Most of these are for debugging.

Tracing program flow:
```

def trace(func):
    def wrapper(*args):
        print("Calling: %s..." % func.__name__)
        return func(*args)
    return wrapper

@trace
def myFunc():
    print "Here I am"

myFunc()

```

Counting function calls:
```

def count(func):
    class static:
        calls = 0
    def wrapper(*args):
        static.calls += 1
        print("'%s', call #%i" % (func.__name__, static.calls))
        return func(*args)
    return wrapper

@count
def func1():
    pass

@count
def func2():
    pass

for i in xrange(15):
    if not (i % 5):
        func1()
    else:
        func2()

```

This can also be turned into a call collector so you can catch all of the calls and analyze them later:
```

class Tracer:

    def __init__(self):
        self.calls = []

    def trace(self, func):
        def wrapper(*args):
            self.calls.append(func.__name__)
            return func(*args)
        return wrapper

    def printCalls(self):
        for call in self.calls:
            print call

tracer = Tracer()

@tracer.trace
def func1():
    pass

@tracer.trace
def func2():
    pass

func1()
func1()
func2()

tracer.printCalls()

```

Function overloading / dispatching. Guido covers a more interesting version of this [here]("http://www.artima.com/weblogs/viewpost.jsp?thread=101605").
```

class Function:

    def __init__(self):
        self.funcs = {}

    def overload(self, *types):
        def decorator(func):
            self.funcs[types] = func
            def wrapper(*args):
                return func(*args)
            return wrapper
        return decorator

    def __call__(self, *args):
        types = tuple(arg.__class__ for arg in args)
        try:
            return self.funcs[types](*args)
        except:
            raise TypeError("No function for arguments: %s" % str(args))

test = Function()

@test.overload(int)
def _test(x):
    print("int function")

@test.overload(int, int)
def _test(x, y):
    print("int, int function")

@test.overload(float)
def _test(x):
    print("float function")

@test.overload(str)
def _test(x):
    print("string function")

test(100)
test(1.0)
test("Hello world")
test(100, 200)
test([1, 2, 3], {"a": 7})

```

Profiling (you could also combine this with the call collector and create a pretty useful debugging tool):
```

import time
import random

def profile(func):
    def wrapper(*args):
        start = time.time()
        ret = func(*args)
        finish = time.time()
        name = func.__name__
        print("'%s' took: %0.5fms" % (name, (finish-start) * 1000))
        return ret
    return wrapper

@profile
def shuffle(lst):
    for i in xrange(len(lst)-1, 0, -1):
        j = random.randint(0, i)
        lst[i], lst[j] = lst[j], lst[i]

@profile
def sort(lst):
    for i in xrange(len(lst) - 1):
        low = i
        for j in xrange(i + 1, len(lst)):
            if lst[j] < lst[low]:
                low = j
        lst[i], lst[low] = lst[low], lst[i]

for size in [16, 32, 64, 128, 256, 512]:
    print("===== Testing size: %i =====" % size)
    lst = range(size)
    shuffle(lst)
    sort(lst)

```

Those are a few of the ones I could think of. I would definitely be interested in any ideas anyone else has.

---

### Post by Quikee on 2008-01-18
Function input parameter Type checking. This is what I came up with:

[PHP]
#!/usr/bin/env python 
import unittest as ut

def typeCheck(*types):
	def decorator(func):
		def wrapper(*parameters):
			for index, parameter in enumerate(parameters):
				if not isinstance(parameter, types[index]):
					raise TypeError, ("Invalid input parameter! Expected: %s got: %s" %(types[index], type(parameter)))
			return func(*parameters)
		return wrapper
	return decorator

if __name__ == "__main__":
	class TypeCheckDecoratorTest(ut.TestCase):
		def testNoParameters(self):
			@typeCheck()
			def testFunction():
				pass
			
			try:
				testFunction()
			except TypeError:
				self.fail("TypeError raised but the input parameter type is correct.")
		
		def testBasicTypes(self):
			@typeCheck(int, float)
			def testFunction(index, value):
				return index, value
			
			try:
				testFunction(100, 10.0)
			except TypeError:
				self.fail("TypeError raised but the input parameter type is correct.")
			
			try:
				testFunction(100, 'abc')
				self.fail("TypeError has not been raised")
			except TypeError:
				pass
				
	ut.main()[/PHP]

---

### Post by Quikee on 2008-01-18
Previous idea extended with a more generic parameter "precondition" checking:

[PHP]
#!/usr/bin/env python 
import unittest as ut

class FunctionPreconditionException(Exception):
	pass
	
def isNotNone(value):
	return value != None
	
def isNumber(value):
	return type(value) in [int, float, complex]

def isPositive(value):
	return value > 0

def isOfType(type):
	def anon(value):
		return isinstance(value, type)
	return anon
	

def preconditionCheck(*checkers):
	def decorator(func):
		def wrapper(*parameters):
			for index, parameter in enumerate(parameters):
				checkersForParameter = checkers[index]
				if type(checkersForParameter) in [list, tuple]:
					if not all([i(parameter) for i in checkersForParameter]):
						raise FunctionPreconditionException, "Function precondition fails for parameter: %d '%s'" % (index, parameter)
				else:
					if not checkersForParameter(parameter):
						raise FunctionPreconditionException, "Function precondition fails for parameter: %d '%s'" % (index, parameter)
			return func(*parameters)
		return wrapper
	return decorator

if __name__ == "__main__":
	class TypeCheckDecoratorTest(ut.TestCase):
		def testNoParameters(self):
			@preconditionCheck(isNotNone, isNumber)
			def testFunction():
				pass
			
			try:
				testFunction()
			except FunctionPreconditionException:
				self.fail("FunctionPreconditionException raised unexpectedly - ")
				
		def testBasicTypesWithMultiplePrecondition(self):
			@preconditionCheck((isNumber, isPositive), isNumber, isOfType(str))
			def testFunction(index, value, someString):
				return index, value, someString
			
			try:
				testFunction(100, 10.0, '')
				testFunction(100, 10.0, 'abc')
				testFunction(100, 10.0, 'abc')
				testFunction(100, -10.0, 'abc')
			except FunctionPreconditionException:
				self.fail()
			
			try:
				testFunction(-100, 10.0, 'abc')
				self.fail()
			except FunctionPreconditionException:
				pass
			
			try:
				testFunction(None, 10.0, 'abc')
				self.fail()
			except FunctionPreconditionException:
				pass
			
			try:
				testFunction('abc', 10.0, 'abc')
				self.fail()
			except FunctionPreconditionException:
				pass
				
			try:
				testFunction(100, None, 'abc')
				self.fail()
			except FunctionPreconditionException:
				pass
			
			try:
				testFunction(100, 'abc', 'abc')
				self.fail()
			except FunctionPreconditionException:
				pass
			
			try:
				testFunction(100, 'abc', None)
				self.fail()
			except FunctionPreconditionException:
				pass
			
			try:
				testFunction(100, 'abc', 20)
				self.fail()
			except FunctionPreconditionException:
				pass
				
	ut.main()
[/PHP]

---

### Post by Wybiral on 2008-01-18
> **Quikee said:**
>  ... 

Interesting! Another condition it might benefit from would be "hasAttribute" (could be implemented with "hasattr") so you could use it with a more duck-typed style (e.g. determine if an object has a "__getitem__" method before its allowed to be passed).

---

### Post by Quikee on 2008-01-18
> **Wybiral said:**
> Interesting! Another condition it might benefit from would be "hasAttribute" (could be implemented with "hasattr") so you could use it with a more duck-typed style (e.g. determine if an object has a "__getitem__" method before its allowed to be passed).

Great idea - this is probably one of the most useful one conditions, but maybe with multiple input attributes:

[PHP]
def hasAttributes(*attribute):
    def anon(value): 
        return all([value.hasattr(attribute) for attribute in attributes]) # could also check if it is callable - depends on the needs
    return anon

@preconditionCheck(hasAttributes("startswith", "endswith") )
test('abc'):
[/PHP]

Another use of decorators is for declarative transactions. 
Example:

[PHP]class Transactional(object):
	@staticmethod
	def transactional(function):
		def proxy(*args):
			self.session.beginTransaction()
			try:
				returnValue = function(*args)
			except Exception:
				self.session.rollback()
				raise
			self.session.commit()
			return returnValue
		return proxy
		
	def __init__(self, session):
		self.session = session
		
class SomeObject(Transactional):
	def __init__(self, session):
		Transactional.__init__(self, session)
		
	@Transactional.transactional
	def some(self):
		print "do something in transaction"
	
	@Transactional.transactional
	def someElse(self):
		print "do something in transaction"
		raise Exception
[/PHP]

---

### Post by mathisdermaler on 2008-01-20
I did not know about that.  Definitely one of the simplest and most elegant ways of doing aspect-orient programming.

---

### Post by Wybiral on 2008-03-12
Memoize a function (try running this WITHOUT the decorators!):
```

def memoized(func):
    def inner(*args):
        try:
            return inner.cache[args]
        except KeyError:
            value = inner.cache[args] = func(*args)
            return value
        except TypeError:
            return func(*args)
    inner.cache = {}
    return inner


@memoized
def fib(n):
    return n if n < 2 else fib(n - 1) + fib(n - 2)


@memoized
def binomial(m,n):
    if m < 0 or n > m:
        return 0
    if n == 0 or m == n:
        return 1
    return binomial(m - 1, n) + binomial(m - 1, n - 1)


print fib(100)
print binomial(40, 20)

```

You can also retrieve the cache (in case you want to save it or something) using function.cache to get the dictionary. You may also clear the cache using function.cache.clear() if you need to free up some memory (it also wouldn't be hard to have it automatically overwrite old cache after a certain limit).

---

### Post by imdano on 2008-03-12
I didn't write either of these (found them in the source for [Exaile](www.exaile.org)), but I've found them to be useful.
[php]

def threaded(f):
    """
        A decorator that will make any function run in a new thread
    """
    def wrapper(*args, **kwargs):
        t = threading.Thread(target=f, args=args, kwargs=kwargs)
        t.setDaemon(True)
        t.start()

    wrapper.__name__ = f.__name__
    wrapper.__dict__ = f.__dict__
    wrapper.__doc__ = f.__doc__

    return wrapper

def synchronized(func):
    """
        A decorator to make a function synchronized - which means only one
        thread is allowed to access it at a time
    """
    def wrapper(self,*__args,**__kw):
        try:
            rlock = self._sync_lock
        except AttributeError:
            from threading import RLock
            rlock = self.__dict__.setdefault('_sync_lock',RLock())
        rlock.acquire()
        try:
            return func(self,*__args,**__kw)
        finally:
            rlock.release()
    wrapper.__name__ = func.__name__
    wrapper.__dict__ = func.__dict__
    wrapper.__doc__ = func.__doc__
    return wrapper[/php]

---

### Post by jespdj on 2008-03-13
Aha. I'm not really a Python programmer (I'd like to learn it someday), but Java has a similar feature named annotations (since Java 5). One use for annotations is [aspect-oriented programming]("http://en.wikipedia.org/wiki/Aspect-oriented_programming") (I'm not sure if you really want to do that all the time).

At work I currently use annotations in a Java web application. I have a handler class that contains a number of methods, each of those methods is to handle a certain action on the web page. I made an annotation @WebAction to connect actions to methods in the handler class. When a request comes in, a servlet looks up the method corresponding to the action and calls it. It looks something like this:
[PHP]public class ActionHandlers {
    @WebAction("save_details")
    public String actionSaveDetails() {
        // Get form data and save it...

        // Return the name of the screen that should be displayed next
        return "thank_you";
    }
}[/PHP]
WIth this, it is very easy to connect up actions on the web page to Java code on the server - all you need to do is write a method and add an annotation to it.

You can also use this for a normal GUI (not web) application, for example to attach button click handlers to buttons etc.

---

### Post by Can+~ on 2008-03-13
Awesome, never knew about this thing. Also, looking for a tutorial on them, I found a slide show with some of some features of python:

[http://www.python.ie/blackmagic/](http://www.python.ie/blackmagic/)

---

### Post by Wybiral on 2008-03-13
I just thought of another way to memoize a Python function. This one doesn't use decorators, but takes advantage of the fact that dictionaries are mutable (and when mutable types are used as default arguments they essentially become static).

```
from time import time

def fib1(n, cache={0: 0, 1: 1}):
    if n not in cache:
        cache[n] = fib1(n - 1) + fib1(n - 2)
    return cache[n]

def fib2(n):
    return n if n < 2 else fib2(n - 1) + fib2(n - 2)

beg = time()
value = fib1(32)
end = time()
print "fib1: %0.5f ms" % ((end-beg) * 1000)

beg = time()
value = fib2(32)
end = time()
print "fib2: %0.5f ms" % ((end-beg) * 1000)
```

---

