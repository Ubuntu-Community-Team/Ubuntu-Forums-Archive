---
title: "[Python] memoization of class methods"
date: 2009-08-27
forum: Programming Talk
---

### Post by unutbu on 2009-08-27
Is there a way to modify this "memoized" class so that it can decorate class methods?
When I run
[PHP]
#!/usr/bin/env python
class memoized(object):
   """
   source: http://wiki.python.org/moin/PythonDecoratorLibrary#Memoize
   Decorator that caches a function's return value each time it is called.
   If called later with the same arguments, the cached value is returned, and
   not re-evaluated.
   """
   def __init__(self, func):
      self.func = func
      self.cache = {}
   def __call__(self, *args):
      try:
         return self.cache[args]
      except KeyError:
         self.cache[args] = value = self.func(*args)
         return value
      except TypeError:
         # uncachable -- for instance, passing a list as an argument.
         # Better to not cache than to blow up entirely.
         return self.func(*args)
   def __repr__(self):
      """Return the function's docstring."""
      return self.func.__doc__


class A(object):
    @memoized
    def f(self,a):
        pass

a=A()
a.f(1)
[/PHP]
I get this error
```
Traceback (most recent call last):
  File "/home/unutbu/pybin/test.py", line 33, in <module>
    a.f(1)
  File "/home/unutbu/pybin/test.py", line 17, in __call__
    self.cache[args] = value = self.func(*args)
TypeError: f() takes exactly 2 arguments (1 given)

```

I think the error arises from the fact that self.func saves A.f as a plain function and not as a bound method. So when I call self.func(*args), I'm calling A.f(1) and the class instance, a, is not getting passed to f.

How does one get around this problem?

---

### Post by unutbu on 2009-08-27
Well, it's not pretty, but here is a work-around:

[PHP]class A(object):
    def f(self,a):
        print('Only once')
        return 2
    def __init__(self):
        self.f=memoized(self.f)

a=A()
print(a.f(1))
# Only once
# 2
print(a.f(1))
# 2[/PHP]

Since A.f is an unbound method, we don't really want to memoize it.
If we wait for the class instance to create the bound method self.f,
and then memoize self.f, then memoization works.

You don't get to use the pretty decorator syntax, and this separates the true 
definition of self.f from the "def f" block, but it works.

---

### Post by codysacoder on 2010-01-02
I know this is an old-ish post but I came up with a decorator solution that works with both normal functions and instance methods. It uses a descriptor to avoid using the workaround you mentioned. This is [also on github.]("https://gist.github.com/267733/8f5d2e3576b6a6f221f6fb7e2e10d395ad7303f9")
[PHP]import functools

class memoize(object):
    def __init__(self, func):
        self.func = func
        self.memoized = {}
        self.method_cache = {}
    def __call__(self, *args):
        return self.cache_get(self.memoized, args,
            lambda: self.func(*args))
    def __get__(self, obj, objtype):
        return self.cache_get(self.method_cache, obj,
            lambda: self.__class__(functools.partial(self.func, obj)))
    def cache_get(self, cache, key, func):
        try:
            return cache[key]
        except KeyError:
            cache[key] = func()
            return cache[key]

class Adder(object):
    @memoize
    def add(self, arg1, arg2):
        print 'CALCULATING', arg1, '+', arg2
        return arg1 + arg2


@memoize
def subtract(arg1, arg2):
    print 'CALCULATING', arg1, '-', arg2
    return arg1 - arg2

def main():
    print subtract(10, 5)
    print subtract(10, 5)

    adder1 = Adder()
    adder2 = Adder()
    print adder1.add(5, 5)
    print adder1.add(5, 5)
    print adder2.add(5, 5)
    print adder2.add(5, 3)

if __name__ == '__main__':
    main()
[/PHP]

---

