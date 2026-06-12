---
title: "Initialization of variable in python?"
date: 2009-08-26
forum: Programming Talk
---

### Post by 25an on 2009-08-26
Hi!

I'am new to python and there is one question that have not yet found an answer for. What should I initialize a class variable to? 

Many times now I have required a global class variable so I can use it
in the other classes also. I initialize this variable at the top of the file and set it to None like this:

ClassAObject=None

Then in the main function I create the object like this:

def main():
   global ClassAObject
   ....
   ...
   ClassAObject = ClassA()
   ...
   ..

The in another class function I require the variable so I call it 
class ClassB()
   global ClassAObject
   ..
   ....
   def somefunc(self):
      ClassAObject.somotherfunc()  

This will cause an exception AttributeError: 'NoneType' object has no attribute 'soneotherfunc'. Is there a better way to initialize a global variable then None?

---

### Post by 25an on 2009-08-26
Sorry about this I found the error after reading this:

"In Python, variables that are only referenced inside a function are implicitly global. If a variable is assigned a new value anywhere within the function&#8217;s body, it&#8217;s assumed to be a local. If a variable is ever assigned a new value inside the function, the variable is implicitly local, and you need to explicitly declare it as global.

Though a bit surprising at first, a moment&#8217;s consideration explains this. On one hand, requiring global for assigned variables provides a bar against unintended side-effects. On the other hand, if global was required for all global references, you&#8217;d be using global all the time. You&#8217;d have to declare as global every reference to a builtin function or to a component of an imported module. This clutter would defeat the usefulness of the global declaration for identifying side-effects." [http://effbot.org/pyfaq/what-are-the-rules-for-local-and-global-variables-in-python.htm](http://effbot.org/pyfaq/what-are-the-rules-for-local-and-global-variables-in-python.htm)

Any thoughts about the use of global variables in python is appreciated.

---

### Post by kpkeerthi on 2009-08-26
If you are programming OOPS-way w/ classes, there will be no practical need for global variables.

---

### Post by Tony Flury on 2009-08-26
One technique i use is a local variable in a module as the class, with a factory function to create or provide the reference to the instance

```

instance = None

def GetSingleInstance():
    if instance is None:
        instance = MyClass()
     return instance


class MyClass():
    def __init(self)__:
        pass

    def do_stuff():
        pass

``` 

This way although effectively you have a global, it is hidden behind a factory function, and the factory function is the thing that is in global scope : as "module.GetSingleInstance() - just need to make sure that all of your code calls the factory function.

You can extend this to provide things like names against objects, so you can refer to an object with a string (or number) - basically the factory function maintains the dictionary.

---

### Post by koonsolo on 2009-08-26
> **Tony Flury said:**
> One technique i use is a local variable in a module as the class, with a factory function to create or provide the reference to the instance

Using a [singleton]("http://en.wikipedia.org/wiki/Singleton_pattern") is probably more OO friendly. You can find plenty of python singleton implementations on Google.

---

