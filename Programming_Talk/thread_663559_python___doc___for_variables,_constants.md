---
title: "python: __doc__ for variables, constants"
date: 2008-01-10
forum: Programming Talk
---

### Post by aquavitae on 2008-01-10
Can anyone suggest a way I can add a __doc__ to a variable.  I have a module which provides accessibility to python scripting within my app, i.e. it has a bunch of functions and variables which are available to the user. I want to create a help function, and the easiest way to do that would seem to be to iterate through __dict__ and print __doc__ for each function, but this does not work for variables.  I'd also like to restrict write access to some variables, i.e. make them constants, but that's not so important.

Any suggestions on how I can create a variable with a __doc__?

---

### Post by popch on 2008-01-10
> **aquavitae said:**
> I'd also like to restrict write access to some variables, i.e. make them constants, but that's not so important.

I can offer a suggestion to that one: in OOP, it is commonly used practice to use instance or class methods instead of constants. The object holding the variable can still change it, all other objects will only access the value through a function call.

---

### Post by aquavitae on 2008-01-10
I'd thought of something like that, but the syntax gets a bit messy, especially for user scripting, compare [code]print 3 * pi[\code] with [code]print 3 * pi.value()[\code]To the user, pi.value() makes no sense. A plain function would be better, but it wouldn't work for variables as there is no easy way to assign it.

---

### Post by popch on 2008-01-10
> **aquavitae said:**
> I'd thought of something like that, but the syntax gets a bit messy, especially for user scripting, compare ```
print 3 * pi[\code] with [code]print 3 * pi.value()[\code]To the user, pi.value() makes no sense. A plain function would be better, but it wouldn't work for variables as there is no easy way to assign it.

try [code]print 3 * myMathConstants.pi()
```

---

### Post by engla on 2008-01-10
Look into the module pydoc, and also look if pydoc.help() is sufficient (this is the normal interpreter help() function).

Also in python you can use **Properties** to make attributes have member variable semantics but hide the logic in getter/setter functions. You only need the getter in this case if the value of pi is constant ;-)

---

### Post by aquavitae on 2008-01-11
Thanks for the suggestion - pydoc looks useful, but I still need to provide documentation for a variable.  ```
print 3 * myMathConstants.pi()[\code] is ok, perhaps better abbreviated to [code]print 3 * c.pi[\code] but its means a rather messy implemetation, def pi() would be easier and more sensible I think.  So far the best I've come up with is this:
[code]
class Var:
   
   class ConstError(TypeError):
      pass
   
   def __init__(self, value, doc, const=False):
      self.__value = value
      self.__doc__ = doc
      self.__const = const
      
   def __call__(self, value=None):
      if value is not None:
         if self.__const:
            raise self.ConstError, 'Cannot assign value to constant'
         else:
            self.__value = value
      return self.__value

```
Still can't get rid of those parenthases though :D

---

### Post by aquavitae on 2008-01-21
I've redesigned things slightly, so now I want to add a __doc__ to a class attribute.  It seems that the obvious way to do this is to use properties (python 2.5).  But because I'm lazy and I have quiet a lot of properties, I don't really want to write a whole lot of similar get and set functions.  My idea is to use generic get and set functions that take an additional argument specifying the attribute name, but then I can't use it in property() because I have the wrong number of arguments. Is there a way to do something like this:
```

class MyClass:
  def get(self, name):
    return self.__dict__[name]
  def set(self, name, value):
    self.__dict__[name] = value
  x = property(get with name='_x', set with name='_x')

```
I've tried partial(), but I need to pass it an instance too, which I don't have when I'm declaring the function.

---

### Post by jfinkels on 2008-01-21
You probably want to look at pydoc.

---

### Post by pmasiar on 2008-01-21
> **aquavitae said:**
>  I don't really want to write a whole lot of similar get and set functions.  


Found somewhere at Python FAQs:
> 
Q: Do I need getters/setters like in java?

A: NO! use `__get__` method on properties. Read the docs for the built in `property()` function. It's a nice mechanism to actually avoid all those getters and setters because you can turn "simple" attributes into "computed" attributes without changing the API of the objects.

---

