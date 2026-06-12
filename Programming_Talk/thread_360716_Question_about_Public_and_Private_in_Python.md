---
title: "Question about Public and Private in Python"
date: 2007-02-13
forum: Programming Talk
---

### Post by thenetduck on 2007-02-13
When making a class in Python how do you make one function definition public or private? Same thing with things like static ect. I can't really image not having them? Thanks, 

 The Net Duck

---

### Post by rickardg on 2007-02-13
Prefix the variable name with __ (two underscores) or more.

```
class Foo():
     def bar(self):
        print "bar() called"

    def __gorp(self):
        print "gorp() called"


```

Let's try it out:

```

>>> f = Foo()
>>> f.bar()
bar() called
>>> f.__gorp()

Traceback (most recent call last):
  File "<pyshell#14>", line 1, in <module>
    f.__gorp()
AttributeError: Foo instance has no attribute '__gorp'
>>> 
```

Seems to do what we want, but since python only implements private members using a pretty simple [name mangling]("http://en.wikipedia.org/wiki/Name_mangling") scheme it is quite easy to access f.gorp().

```
>>> f._Foo__gorp()
gorp() called
>>> 
```

Have a look at the [Python tutorial]("http://docs.python.org/tut/node11.html#SECTION0011600000000000000000") for more info and at this [Python Cookbook recipe]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/496930") for a (not completely successful) attempt to implement more rigorous access control.

---

