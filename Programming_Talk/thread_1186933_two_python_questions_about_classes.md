---
title: "two python questions about classes"
date: 2009-06-14
forum: Programming Talk
---

### Post by NetSkay on 2009-06-14
hello...
i have 2 question to which i was unable to find an answers to, so thnx in advance for any responses

first question is on inheritance, i use @classmethod to make a method callable directly from class without the need for instancing the class, but is there a way that i can just omit self from the methods to make them directly callable, or can i even have a class that i can call methods from without instancing it first? and what is the difference between having self in a method within a class and not having self, is it for encapsulation because without self i cant call it from within the class either...

my second question is on extending classes, i have 2 classes within a .py file and i want to extend class A with class B, aka
class A(B):
   def mymethod...

but when i instance class A and i try to call something from class B through class A instance, i get a tracestack with error saying i need to call method with class B instance... then whats the point of extending? or does extending work only for python lib classes and relates to my instancing question above...

thank you

---

### Post by nvteighen on 2009-06-14
> **NetSkay said:**
> hello...
i have 2 question to which i was unable to find an answers to, so thnx in advance for any responses

first question is on inheritance, i use @classmethod to make a method callable directly from class without the need for instancing the class, but is there a way that i can just omit self from the methods to make them directly callable, or can i even have a class that i can call methods from without instancing it first? and what is the difference between having self in a method within a class and not having self, is it for encapsulation because without self i cant call it from within the class either..

Hm... it seems like you want to use @staticmethod. That will make your method not accept any implicit argument (either class or instance). The problem with that is that if you want to enter any class/instance data, you'll have to pass it explicitly as an argument.

The reason of explicit self is that in good programming, only the parameters of a certain procedure should be the factors to consider to determine the result and nothing else. Otherwise, the class/instance data will act as restricted globals and make debugging much more difficult.

It's actually more of a matter of order than anything else.

> 
my second question is on extending classes, i have 2 classes within a .py file and i want to extend class A with class B, aka
class A(B):
   def mymethod...

but when i instance class A and i try to call something from class B through class A instance, i get a tracestack with error saying i need to call method with class B instance... then whats the point of extending? or does extending work only for python lib classes and relates to my instancing question above...


Ah, because you have to explicitly instantiate the class you're inheriting from:

```

class A(B):
    def __init__(self):
        B.__init__(self)
        ...
    
    def mymethod(self):
        ...

```

---

### Post by NetSkay on 2009-06-14
> **nvteighen said:**
> 
The reason of explicit self is that in good programming, only the parameters of a certain procedure should be the factors to consider to determine the result and nothing else. Otherwise, the class/instance data will act as restricted globals and make debugging much more difficult.

It's actually more of a matter of order than anything else.


what do you mean?

and so can i event omit self at all from a method to make it only accessible from within the class... i donno why self is so confusing, and if its always absolutely necessary for a method to have self, then why does it always have to be typed and not assumed automatically by the python interpreter?

---

### Post by nvteighen on 2009-06-14
> **NetSkay said:**
> what do you mean?

and so can i event omit self at all from a method to make it only accessible from within the class... i donno why self is so confusing, and if its always absolutely necessary for a method to have self, then why does it always have to be typed and not assumed automatically by the python interpreter?
No. Python forces you to use **self** if you mean your function to be an **instance method**. Why? Because the idea in structured programming is that only stuff in parameters should have access to affect a function's behaivor. In a method, of course, you expect access to all object's data, so in Python is logical that you have to pass **self** as a parameter... and so you'll always follow the rule that only parameters affect a function's behaivor and nothing else (that's why globals are evil).

Other languages (C++, Objective-C, for example) choose to assume **self**. And not only that, you can access the object's data by just referring to the variable/method's name directly. Yes, this may be a bit more "practical", but results in variables appearing anywhere without a declaration in the given scope just because they are attributes... Therefore, looking a bit like "restricted" globals.

Perl's OOP approach is similar to Python's, but even more explicit as you have to define what your **self** is by "blessing" it into a package/class... :p

---

### Post by delfick on 2009-06-14
also, python doesn't force you to use the word 'self'.
It's just a convention (that everyone should use :))

so if I had a class (and while you can, you'd never do this) I could replace 'self' with 'this'

[php]
class example(object):
    def __init__(this, a, b):
        this.a = a
        this.b = b

    def printStuff(this):
        print '%s %s' % (this.a, this.b)

newExample = example("hello", "there")
newExample.printStuff()
[/php]

what happens when I call printStuff is that an instance of the newExample object is automatically passed in as the first parameter.

By convention, this first parameter should be called 'self'


Also note how it's exactly the same as calling 'example.printStuff(newExample)' :)

---

### Post by slavik on 2009-06-15
> **nvteighen said:**
> No. Python forces you to use **self** if you mean your function to be an **instance method**. Why? Because the idea in structured programming is that only stuff in parameters should have access to affect a function's behaivor. In a method, of course, you expect access to all object's data, so in Python is logical that you have to pass **self** as a parameter... and so you'll always follow the rule that only parameters affect a function's behaivor and nothing else (that's why globals are evil).

Other languages (C++, Objective-C, for example) choose to assume **self**. And not only that, you can access the object's data by just referring to the variable/method's name directly. Yes, this may be a bit more "practical", but results in variables appearing anywhere without a declaration in the given scope just because they are attributes... Therefore, looking a bit like "restricted" globals.

Perl's OOP approach is similar to Python's, but even more explicit as you have to define what your **self** is by "blessing" it into a package/class... :p
in the case of Perl, bless is magic, so you kind of have to do it (although it is done implicitly on class calls), example: new MyClass(); calls MyClass::new(), it might as well be: foo MyClass(); in Perl, a constructor is anything that calls bless.

As for implicing 'self' in C++ and Java they are called 'this' and if you class is static (as is with the case of Java's 'main' then that class cannot have any non-static variables (or something, I forget, but I do remember lots of errors due to static funcs accessing a non-static class variable).

btw, I am sure I got something wrong in this post. if you know what it is please correct me.

---

