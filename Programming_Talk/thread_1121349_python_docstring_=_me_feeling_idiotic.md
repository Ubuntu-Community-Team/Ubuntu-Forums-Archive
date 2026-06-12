---
title: "python docstring = me feeling idiotic"
date: 2009-04-09
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-04-09
I am REALLY confused on docstrings in python. 

Im currently using the _A Byte of Python Guide_  but for some reason the docstring is confusing. So far everything has been fine.  

oh, and can you please make the explanation easy and simple, so a little 13-year-old like me can understand it?

---

### Post by soltanis on 2009-04-09
So far as I understand them, they're just strings you put into a special variable that quickly describe what whatever you're writing does, so that later on someone can read it and ignore it.

---

### Post by flyingsliverfin on 2009-04-09
implying they're useless?

---

### Post by ghostdog74 on 2009-04-10
> **flyingsliverfin said:**
> implying they're useless?

no they are not. if put inside functions/classes, 
```

def func_a():
   ''' this is some help to explain func_a usage '''

```
it provides "help" for those that use the function (help(func_a))

it can also be used to declare multiline variable,, eg
```

variable = """
 this is a multiline
 variable %s. 
""" % "string"

```

---

### Post by flyingsliverfin on 2009-04-10
so in the Ex (taken from the tutorial on your sig)

print my_function.__doc__

if you are just calling up a function, why the print? and whts up with the ._doc_?

hey won't be online till tomorrow (just add about 12 or 14 hours to see when it'l be tomorrow for me) so don't expect answers today

---

### Post by nvteighen on 2009-04-10
> **flyingsliverfin said:**
> so in the Ex (taken from the tutorial on your sig)

print my_function.__doc__

if you are just calling up a function, why the print? and whts up with the ._doc_?

hey won't be online till tomorrow (just add about 12 or 14 hours to see when it'l be tomorrow for me) so don't expect answers today
It's not a function, it's an attribute of your function object. In Python, functions are also objects and have attributes (have you learned some of OOP yet? If not, don't worry... it will make sense to you when you get to it). That attribute is just a string, so you need the "print" to show it.

---

### Post by flyingsliverfin on 2009-04-10
right... do I really need them? I could just skip them. It's not like someone my age in 7th grade needs to document all the functions I make.

---

### Post by wmcbrine on 2009-04-10
Yeah you do. Not *all* the functions, just all the ones you want to understand later, or want someone else to understand, without having to parse through all the code to figure out what it's doing. (Sometimes even that isn't enough.)

A docstring is basically just a comment, with extra oomph via help() and other mechanisms. And comments are not useless. Don't ever think that.

(*Some* comments *are* useless, of course:

```

a += 1 # add one to a

```

Don't do that.)

Both overcommenting and undercommenting are bad. It will take time to get a feel for the right balance.

---

### Post by Reiger on 2009-04-10
When you write code for others to use, it is important that others know how to use that code; and in particular what code to use and what to leave alone, what to make your own versions of and what is best kept default. Now that is what API documentation is for.

Simply put a docstring is your own API documentation to your own function or class or member variable/property. In Java and languages influenced by Java's Javadoc system you see a similar concept using a special kind of comment:
```

/**
 MyClass
 @author Me
*/
public class MyClass {
}

```

In an reasonably competent Java IDE you will likely see a popup when you mouse over MyClass that spits out that comment with some nice formatting.

However, with Python you can go a step further; because as nvteighen mentions the String is a property of the Function object. This means that the String is available to your code (and you can tinker with it).

---

### Post by soltanis on 2009-04-10
What I meant to imply was, you should use them, but that all too often I've seen people completely ignore them (and end up screwing up the code because of it).

If you'd like a guideline about commenting, think of it this way:

Comments point out what something does. So when you write say a function (or a block of code, or something) that you're going to reuse (i.e. use more than once), you should probably write a quick comment, or docstring, describing what the heck it is your function does, what parameters it takes, and what it returns back. When you come back in 2 weeks to that code you'd like to use again, you'll be glad you did, so you know what its going to do without necessarily having to re-read it.

What you should not do (and this is relevant in C moreso than it is in python, probably) is
- write comments to separate sections of code (because if your function is that long, you should really consider splitting it up)
- comment on that does something obvious (already explained)
- write a comment that explains how something works (because if you can't read your code and understand what it's doing, more likely than not you screwed something up while writing it)

---

### Post by flyingsliverfin on 2009-04-11
thanks everyone. 

I think I get docstrings more now!

---

### Post by Greyed on 2009-04-11
> **soltanis said:**
> - comment on that does something obvious (already explained)
- write a comment that explains how something works (because if you can't read your code and understand what it's doing, more likely than not you screwed something up while writing it)

Although these two are tempered with the big question of why.  If something seems out of place sometimes it is best to comment on why you're doing it.  EG:

```

a = a + 1 # Adding 1 to a (bad, describes an obvious what)

a = a + 1 # Adjusting for index starting at 1 instead of 0 (good, describes why the 1 is being added)

```

---

### Post by nvteighen on 2009-04-11
My comment/docstring guidelines are more or less the following. Maybe these can help you:

1. Docstrings (comment at the beginning of function) for commenting the interface information of what a certain function does. This means: what does it do, what are the arguments meant to be and what does it return and different meanings of the possible return values. I never put implementation information on them. Try to keep these as longest as possible.

2. Comments for implementation notes. Usually, a good code is self-explaining, but sometimes you need to clarify what you're doing... Usually, it's about why you are doing something, rather than what (because that's the easiest). Try to keep these as shortest as possible.

I follow these even in C, C++ or other languages that do not support "docstrings", because it orders things a lot: you don't have interface and basic explanations in the code's body, but all together at the beginning.

---

### Post by gnuman on 2009-04-11
> **flyingsliverfin said:**
> thanks everyone. 

I think I get docstrings more now!

Python makes it very easy to use docstrings to test your code, also.  That may not seem real important now, but when projects get large.... 


[http://docs.python.org/library/doctest.html](http://docs.python.org/library/doctest.html)

---

