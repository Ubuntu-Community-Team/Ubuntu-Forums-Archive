---
title: "Python 3"
date: 2007-08-31
forum: Programming Talk
---

### Post by triptoe on 2007-08-31
can someone explain these changes in more detail: 

>     * moving map, filter and reduce out of the built-in namespace (the rationale being that map and filter are expressed more clearly as list comprehensions, and reduce more clearly as an accumulation loop)
    * adding support for optional function annotations that can be used for informal type declarations or other purposes[1]
    * unifying the str/unicode types, and introducing a separate mutable bytes type
    * converting built-ins to returning iterators (instead of lists), where appropriate
    * removing backward-compatibility features like classic classes, classic division, string exceptions, and implicit relative imports


---

### Post by ssam on 2007-08-31
i assume you are asking as someone who writes programs in python. (the differences are probably more complex for people who right python modules).

> moving map, filter and reduce out of the built-in namespace (the rationale being that map and filter are expressed more clearly as list comprehensions, and reduce more clearly as an accumulation loop)

any expression using these functions can be converted to one that uses list comprehension. if you still want to use the old functions it sounds like they will be avaliable as a module.

some more info at
[http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

> *adding support for optional function annotations that can be used for informal type declarations or other purposes[1]
* unifying the str/unicode types, and introducing a separate mutable bytes type

not too sure about these.

```
converting built-ins to returning iterators (instead of lists), where appropriate
```

currently there are functions like range() and xrange()

range() makes a list, xrange() makes an iterator. if you do something like
```

for x in range(10**10):
    print x

```

the list that gets created by range will consume a large amount of memory. if you used xrange() the values for x are only created as they are needed.

in python 3 range() will behave as xrange does in python 2.x

> 
removing backward-compatibility features like classic classes, classic division, string exceptions, and implicit relative imports

python 2.2 introduced a new style of classes, but the classic style was kept for backwards compatability. unless you are using advanced OO features they behave pretty much the same. i started python at version 2.3, and all the docs advised to use the new style eg:
```

class Foo(object): 

```

for programs using old style classes, they will need to convert them. i think this is a trivial task unless they have been using fancy OO features (things liek multiple inheritance).

the division one fixes 
```

>>> 5/2
2
>>> 5/2.0
2.5

```
which confuses people who don't come from a C background.

currently you can import the new stlye division
```

>>> from __future__ import division
>>> 5/2
2.5
>>> 5//2
2
>>>

```

there seems to be a well designed upgrade path. see [http://www.artima.com/weblogs/viewpost.jsp?thread=208549](http://www.artima.com/weblogs/viewpost.jsp?thread=208549)

---

### Post by pmasiar on 2007-08-31
Thanks ssam, let me dig out the rest:

> 
* adding support for optional function annotations that can be used for informal type declarations or other purposes[1]
[http://www.python.org/dev/peps/pep-3107/](http://www.python.org/dev/peps/pep-3107/) 

Semantics is let for 3rd-party libraries to hash out. I know some libraries use it to make numeric calculations more effective. So nothing to worry about - you can safely ignore that if you don't use it, just know the syntax so you will not be confused if someone does use it.

> 
* unifying the str/unicode types, and introducing a separate mutable bytes type


see [http://www.artima.com/weblogs/viewpost.jsp?thread=208549](http://www.artima.com/weblogs/viewpost.jsp?thread=208549) , "Unicode, Codecs and I/O" :
- all strings will be unicode and immutable. Unicode "glyph" can by more than one byte long, so need for separate bytes: [http://www.python.org/dev/peps/pep-0358/](http://www.python.org/dev/peps/pep-0358/)

Read [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/articles/Unicode.html) by famous Joel Spolsky (and subscribe to his posts!) and [ about Unicode and character encodings](http://everydeveloper.blogspot.com/2007/06/about-unicode-and-character-encodings.html)

---

### Post by triptoe on 2007-08-31
> **pmasiar said:**
> Thanks ssam, let me dig out the rest:


[http://www.python.org/dev/peps/pep-3107/](http://www.python.org/dev/peps/pep-3107/) 

Semantics is let for 3rd-party libraries to hash out. I know some libraries use it to make numeric calculations more effective. So nothing to worry about - you can safely ignore that if you don't use it, just know the syntax so you will not be confused if someone does use it.



see [http://www.artima.com/weblogs/viewpost.jsp?thread=208549](http://www.artima.com/weblogs/viewpost.jsp?thread=208549) , "Unicode, Codecs and I/O" :
- all strings will be unicode and immutable. Unicode "glyph" can by more than one byte long, so need for separate bytes: [http://www.python.org/dev/peps/pep-0358/](http://www.python.org/dev/peps/pep-0358/)

Read [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](http://www.joelonsoftware.com/articles/Unicode.html) by famous Joel Spolsky (and subscribe to his posts!) and [ about Unicode and character encodings](http://everydeveloper.blogspot.com/2007/06/about-unicode-and-character-encodings.html)

thanks

---

### Post by triptoe on 2007-09-01
What do y'all make of these criticisms of python?

[http://www.osnews.com/comment.php?news_id=18547](http://www.osnews.com/comment.php?news_id=18547)

> * very clear, readable syntax

That's a matter of personnal preference. I don't like the absence of visible block delimiters myself.

* intuitive object orientation

Intuitive? What is that supposed to mean?

* very high level dynamic data types

Oh yeah, even integers are objects, and most of them are builtin, shared instances. So the interpreter carries around pointers to integers and have to dereference them all the time instead of juts manipulating the values directly, all for the sake of the once in a while useful feature of being able to treat thee like objects of the integer class.
They could have done boxing/unboxing to convert a plain, normal, basic integer type into an integer instance as needed.

* extensive standard libraries and third party modules for virtually every task

So extensive that there are even several for the same tasks, including some deprecated ones.

* extensions and modules easily written in C, C++
(or Java for Jython, or .NET languages for IronPython)

Easily written... Yeah, I guess so. From the top of my head:

- they just figured (in 2007) almost all of the places where to use const so we don't need to const_cast every constant string anymore

- they provide horrible macros to do various things (and some of them don't include braces so you have to surround them yourself). They apparently still haven't discovered inline functions, but seeing how they just discovered the const keyword, it may be a while.

- they provide horrendous macros for boolean types that do fugly casting that breaks strict aliasing rule - but you have no alternative to test booleans, so you either have to live with the warning, disable strict aliasing or just screw their macros and do it by hand, thus breaking source level compatibility

- creating a new type is a snap that just requires a ridiculous initializer list with a shitload of zeros and a macro in the middle. Very pretty. A common principle of object orientation is to have opaque structures that are initialized by some function, and you'd think that people designing an OO language would have a grasp of such concepts.

- things have unconsistant naming schemes (new/dealloc, alloc/free).

- the python header has to be included first because they felt they had the right to alter global defines that are used by system headers (imagine if every other library had this kind of requirement)

- you only need to redundantly specify the name of the module you want to create twice.

- almost forgot: explicit reference counting, which is exceedingly stupid and would alone largely suffice to make the api not the least bit user friendly, unlike what fanboys say.

* embeddable within applications as a scripting interface

Thanks, but no thanks. Lua is a cleaner language, more compact, with a non-retarded API, and it's faster to boot.


---

### Post by pmasiar on 2007-09-01
> **triptoe said:**
> What do y'all make of these criticisms of python?

Some people prefer different languages. Looks like the poster is one of the 2% programmers who knows  Python but does not like it. 

> * very high level dynamic data types
Oh yeah, even integers are objects, and most of them are builtin, shared instances. 
So the interpreter carries around pointers to integers and have to dereference them all the time instead of juts manipulating the values directly, all for the sake of the once in a while useful feature of being able to treat thee like objects of the integer class.

IMHO canonical case of using wrong tool. If speed is  serious problem, use C.

> They could have done boxing/unboxing to convert a plain, normal, basic integer type into an integer instance as needed.

And have confusing mess like Java? No thanks.

> * extensive standard libraries and third party modules for virtually every task

So extensive that there are even several for the same tasks, including some deprecated ones.

Well, obviously, this is price of freedom: you made a library, then someone else made better one. What should Python do: forbid to create better third-party libraries? :-)

> * extensions and modules easily written in C, C++ (or Java for Jython, or .NET languages for IronPython)

Easily written... Yeah, I guess so.

Easier than writing extension for .NET under Linux or BSD, or .NET extension running in JVM :-)

Obviously making cross-platform implementations is hard. But with Python, it is at least possible.

> * embeddable within applications as a scripting interface

Thanks, but no thanks. Lua is a cleaner language, 


Wikipedia says that [Lua](http://en.wikipedia.org/wiki/Lua_%28programming_language%29) is one of closest relative  to Python.

"It supports only a small number of atomic data structures such as boolean values, numbers (double-precision floating point by default), and strings. Typical data structures such as arrays, sets, hash tables, lists, and records can be represented using... map (hash)"

"Lua has no built-in support for namespaces and object-oriented programming"

Does Lua have database drivers? Web app framework? package for statistics? Don't think so. 

Lua might be good for some small niche where this poster works, it does not say anything about Python in general. 

Is Lua the silver bullet - future language to rule them all? Unlikely, but if it is, Lua is **very** close to Python (just check the wikipedia), so switching from Python will be easier than from Java or C#. :-)

---

### Post by triptoe on 2007-09-02
Is python really thiss slow?

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all)

20 times slower than C ? does that seem exaggerated??

---

### Post by Smygis on 2007-09-02
> **triptoe said:**
> Is python really thiss slow?

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all)

20 times slower than C ? does that seem exaggerated??

Python is an interpeted language. C is compiled.

Yes Python is a hell of a lot slower then C... But Python modules can be written in C if you need more speed.

---

### Post by pmasiar on 2007-09-02
> **triptoe said:**
> 20 times slower than C ? does that seem exaggerated??

Yes, but so what? If 80% of execution time is spent accessing database, making it in C instead of in Python will make it max 20% faster. And making it work (aka bug-free) will take you 20 times longer in C :-)

---

### Post by triptoe on 2007-09-02
> **pmasiar said:**
> Yes, but so what? If 80% of execution time is spent accessing database, making it in C instead of in Python will make it max 20% faster. And making it work (aka bug-free) will take you 20 times longer in C :-)

Okay but here is one more question.. I have heard.. that C# and .NET are actually pretty fast. In fact that chart shows it as a factor of 3 compared to C.

Will Iron python.. the python implementation of .NET.. be comparable to C# ... the C# implementation of .NET ?

I have heard that in some situations ironpython is actually faster than python. is that true?

---

### Post by ButteBlues on 2007-09-02
> **triptoe said:**
> Okay but here is one more question.. I have heard.. that C# and .NET are actually pretty fast. In fact that chart shows it as a factor of 3 compared to C.

Will Iron python.. the python implementation of .NET.. be comparable to C# ... the C# implementation of .NET ?

I have heard that in some situations ironpython is actually faster than python. is that true?
Yes.

The same applies for IronRuby.

---

### Post by pmasiar on 2007-09-02
> **triptoe said:**
> I have heard that in some situations ironpython is actually faster than python. is that true?

Yes. MSFT hired author of Jython (Jim Hugunin) to implement Python for .NET (IronPython) **and** to teach them how to make .NET runtime more friendly for dynamically typed languages like Python (and recently Ruby).

They did it of course as fighting off Java, but looks like MSFT is the only company which gets it: best way to write programs is to have fast compiled language for libraries (C#.NET), and flexible dynamically typed language(s) to glue together library calls. 

Certainly Sun did not get it: now Sun is trying to catch up with JRuby, but if you think that Jython was first, and Sun ignored Jim from 1999 till IIRC 2004 and was not willing to "waste" money to support Jython. They managed to snatch defeat from jaws of victory. And even now, they **still** support only the smaller player: JRuby. They still don't get it, and think Java will save them, as Java web developers stampede to Ruby.

OK, back to your question:

IronPython is faster, because more effort was sinked to make it faster: MSFT pays couple of people to work on IronPython, and whole lot of developers are paid to optimize .NET for dynamically typed languages. JVM is certainly not interested in it, and CPython does not have the resources - no company finances its development. Google uses Python a lot, and hired couple gurus, but apparently is less interested in developing language runtimes than MSFT is.

---

