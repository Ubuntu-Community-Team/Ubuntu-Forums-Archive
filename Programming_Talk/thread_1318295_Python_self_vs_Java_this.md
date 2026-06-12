---
title: "Python self vs Java this"
date: 2009-11-07
forum: Programming Talk
---

### Post by fiddler616 on 2009-11-07
Hello,

I guess I'd consider myself equally fluent in Python and Java, but I learned OOP in Python first. As such, I'm used to all instance variables being referenced like so: "self.spam"

Now that my CS class is learning OOP (in Java), I feel the urge to treat instance variables the same way: "this.spam". But everyone else (including the teacher) seems to have some kind of this-o-phobia, instead pulling stunts like this:

```

public class Spam
{
    private String flavor;
    public Spam(String flav)
    {
        flavor = flav;
    }
    public String getFlavor()
    {
        return flavor;
    }
}
```
as opposed to my:
```

public class Spam
{
    private String flavor;
    public Spam(String flavor)
    {
        this.flavor = flavor;
    }
    public String getFlavor()
    {
        return this.flavor;
    }
}
```

I have two questions:

1) In terms of *Java style* (whatever Java's version of PEP 8 is), which is preferable?

2) Am I misguided in thinking that it's very good to clearly differentiate between instance variables (by using this) and variables confined to a certain method? And that having two separate variables like "flavor" and "flav" in the same method (which may be more complex than that oneline) is a Bad Idea?

---

### Post by jollysnowman on 2009-11-07
If your data members are the same as the method parameters, clarify using this. If not, make the names of the data members obvious, like myFlavor or _flavor, or instead use parameters like flav_in or f.

Regarding your thread title, Python doesn't really have "self" as Java has "this." You can put whatever name you want there instead of self, and Python will take it.

---

### Post by Can+~ on 2009-11-07
> **jollysnowman said:**
> Regarding your thread title, Python doesn't really have "self" as Java has "this." You can put whatever name you want there instead of self, and Python will take it.

The main issue is not the wording, but how Python expects an explicit reference.

I always prefer explicit [FONT="Courier New"]this[/FONT] when using Java. 

For example, if you have a variable named "something" and the instance has an attribute named "somethingsimilar". I always think is awkward trying to read an assignment "something = 2". Did I just change the local variable or the attribute, which name was each? *goes up to read the declarations* oh right.

On the other hand, having "this.attribute = " makes it clear in my mind that I'm changing attributes.

---

### Post by CptPicard on 2009-11-07
Needless usage of "this" (unless you're using same names as method parameters) is not typical Java style, as the "this" is assumed to implicitly be there if you're not referring to anything in the method-local scope. In Java, you are, after all, always working with some object instance when you're dealing with a non-static method.

Python is different as functions can be unattached to an instance, and they can be attached dynamically at runtime, so the relevant instance has to always be passed in as the explicit "self"...

---

### Post by fiddler616 on 2009-11-07
> **jollysnowman said:**
> If your data members are the same as the method parameters, clarify using this. If not, make the names of the data members obvious, like myFlavor or _flavor, or instead use parameters like flav_in or f.
I could see myself getting confused between flavor and myFlavor. Moreso than I would with an explicit this.
> 
Regarding your thread title, Python doesn't really have "self" as Java has "this." You can put whatever name you want there instead of self, and Python will take it.
Err....
[PHP]>>> class Spam:
...     def __init__(self):
...         self.type = "Bacon"
... 
>>> foo = Spam()
>>> class Eggs:
...     def __init__(self):
...         any_name_I_want.type = "Fried"
... 
>>> bar = Eggs()
Traceback (most recent call last):
    NameError: global name 'any_name_I_want' is not defined[/PHP]

@Can+~ So I won't get accused of programming in Python with Java syntax? Great.

---

### Post by SunSpyda on 2009-11-07
1) The first one, unless there is ambiguity, which then means 'this' is required.

2) Self is needed in Python as it has a broken, non-logical, primitive scoping system. Languages where scope has being implemented properly, it shouldn't be needed except to remove ambiguity.

I really like Python, but its scoping is an abomination (Like Ruby). Perhaps I've been spoiled by C++/C#/Perl 5/Java?

---

### Post by fiddler616 on 2009-11-07
> **CptPicard said:**
> Needless usage of "this" (unless you're using same names as method parameters) is not typical Java style, as the "this" is assumed to implicitly be there if you're not referring to anything in the method-local scope. In Java, you are, after all, always working with some object instance when you're dealing with a non-static method.

Ahh.
But do you have anything to say about the use of two similar-sounding yet different variables?
> 
Python is different as functions can be unattached to an instance, and they can be attached dynamically at runtime, so the relevant instance has to always be passed in as the explicit "self"...
I believe you, but could you please give a short example? I was not aware of the fact that this, er, existed.

---

### Post by fiddler616 on 2009-11-07
> **SunSpyda said:**
> 1) The first one, unless there is ambiguity, which then means 'this' is required.

But what's the definition of ambiguity? I feel like the difference between flavor and flav is pretty ambiguous, but apparently the Greater Java World does not.
> 
2)Self is needed in Python as it has a broken, non-logical, primitive scoping system. Languages where scope has being implemented properly, it shouldn't be needed except to remove ambiguity.

I really like Python, but its scoping is an abomination (Like Ruby).
True confessions: I still don't understand how to make variables in the main body of a program not be global.
[PHP]>>> x = 2
>>> def spam(y):
...     print x + y
>>> spam(3)
5
>>> def spam(x):
...     print x
>>> spam(x)
2
>>> spam(3)
3[/PHP]
x is a problem...

---

### Post by days_of_ruin on 2009-11-07
> **fiddler616 said:**
> I could see myself getting confused between flavor and myFlavor. Moreso than I would with an explicit this.

Err....
[PHP]>>> class Spam:
...     def __init__(self):
...         self.type = "Bacon"
... 
>>> foo = Spam()
>>> class Eggs:
...     def __init__(any_name_I_want):
...         any_name_I_want.type = "Fried"
... 
>>> bar = Eggs()
[/PHP]

@Can+~ So I won't get accused of programming in Python with Java syntax? Great.

You have to change the "self" argument passed to "any_name_I_want" too, like so ^^^. **BUT DON'T DO THIS AS IT WILL CONFUSE EVERYONE AND I WILL HAVE TO SHOOT YOU.**

---

### Post by ssam on 2009-11-07
at least you can't modify main's x, unless you are explicit that you want the global one.

```
>>> x=2
>>> def spam(y):
...     print x
...     x += y
...     print x
... 
>>> spam(3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in spam
UnboundLocalError: local variable 'x' referenced before assignment
>>> def eggs(y):
...     global x
...     print x
...     x += y
...     print x
... 
>>> eggs(3)
2
5
>>> x=2
>>> def foo(y):
...     x=y
...     print x
... 
>>> foo(3)
3
>>> x
2

```

---

### Post by CptPicard on 2009-11-07
@fiddler,

```

import types


class MyClass:
    def __init__(self, data):
        self.data = data


def func(self):
    ''' Prints "data" from any object that has such a field '''
    print self.data


x = MyClass("Hello")
x.printer = types.MethodType(func, x)

x.printer()

```

I just learned that newer versions of Python no longer allow you to just stick any function with first argument assumed to be of the correct type onto any object... it used to be as simple as "x.printer = func". Now that is certainly a regression in the generic design of Python, I do not like this change at all :(

---

### Post by fiddler616 on 2009-11-07
> **days_of_ruin said:**
> You have to change the "self" argument passed to "any_name_I_want" too, like so ^^^.Oh. That makes sense. 
> **BUT DON'T DO THIS AS IT WILL CONFUSE EVERYONE AND I WILL HAVE TO SHOOT YOU.**
Indeed. I believe a public tarring and feathering would be in order.

---

### Post by Can+~ on 2009-11-07
> **CptPicard said:**
> @fiddler,

```

import types


class MyClass:
    def __init__(self, data):
        self.data = data


def func(self):
    ''' Prints "data" from any object that has such a field '''
    print self.data


x = MyClass("Hello")
x.printer = types.MethodType(func, x)

x.printer()

```

I just learned that newer versions of Python no longer allow you to just stick any function with first argument assumed to be of the correct type onto any object... it used to be as simple as "x.printer = func". Now that is certainly a regression in the generic design of Python, I do not like this change at all :(

I had that same discovery the other day, and I didn't like it either. On the other hand, it has the benefit that you can add self-less functions to a class with the older operation.

I can imagine a more pythonic way, would be to define a method named __setmethod__ that you could override to do this, instead of another import. Maybe we should write a PEP about it?

---

### Post by gorilla on 2009-11-07
> **fiddler616 said:**
> But what's the definition of ambiguity? I feel like the difference between flavor and flav is pretty ambiguous, but apparently the Greater Java World does not.
Ambiguity means that different things have the same name, thus the compiler cannot know which one is meant.

> **fiddler616 said:**
> 2) Am I misguided in thinking that it's very good to clearly differentiate between instance variables (by using this) and variables confined to a certain method? And that having two separate variables like "flavor" and "flav" in the same method (which may be more complex than that oneline) is a Bad Idea?
I would guess your instructor might do this for educational purposes? Maybe he doesn't want to discuss scoping rules just yet.

---

### Post by shadylookin on 2009-11-08
Don't make local variables similar to instance variables and you won't really need to worry about removing ambiguity. Unless you have masochistic tendencies there's no point in making your life harder by trying to confuse yourself

---

### Post by SunSpyda on 2009-11-08
> **fiddler616 said:**
> But what's the definition of ambiguity? I feel like the difference between flavor and flav is pretty ambiguous, but apparently the Greater Java World does not.

Ambiguity, as in...
[php]
class Main {
    public static main(String[] args) {
        Account account = new Account();
        account.setName("Tom");
        javax.swing.JOptionPane.showMessageDialog(null, "Name - " + account.getName());
    }
}

class Account {
    protected String name;

    String getName() {
        return name;
    }

    // Here is the ambiguity...
    void setName(String name) {
        this.name = name;
    }
}
[/php]

---

### Post by CptPicard on 2009-11-08
It needs to be noted that the mentioned cases about parameter/instance variable ambiguity are not showstoppers in Java though, the compiler just assumes that the LHS is a member of the object and the RHS is the method parameter.

It does confuse the programmer though :)

---

