---
title: "embedding python in c++"
date: 2007-10-15
forum: Programming Talk
---

### Post by aquavitae on 2007-10-15
I'm sure this is really simple, but I can't work it out.

I want to include a python interpretor in my c++ app.  How would I transfer data in the app to and from python scripts.  E.g. how would I write:
```

**c++:**
int a = 1;
int b = 2;
int c;
**to python:**
c = eval("a + b if a > 0 else 4", {'a' : a, 'b' : b})
*# or*
exec("c = a + b if a > 0 else 4", {'a' : a, 'b' : b, 'c' : c})

```

Not sure if that's clear... Help anyone?

---

### Post by LaRoza on 2007-10-15
As it stands, I am not sure what you are attempting. It looks like using Python is what you want, or finding or writing similar functions for C++.

---

### Post by aquavitae on 2007-10-15
Kinda...  I want to execute a line of python code within c++, optionally returning a value.  I think I'm basically looking for functions in the c++ api that work the same as the eval and exec functions in python.

---

### Post by LaRoza on 2007-10-15
> **aquavitae said:**
> Kinda...  I want to execute a line of python code within c++, optionally returning a value.  I think I'm basically looking for functions in the c++ api that work the same as the eval and exec functions in python.

You should use Python if you want such high level features.

---

### Post by aquavitae on 2007-10-15
The program has already been written in c++.  It would take months to rewrite it in python - I did actually start doing that, but I don't have the time.  Instead I'm starting to slowly rewrite some of the non-core functions in python, but I still need to find out how to execute them.

---

### Post by LaRoza on 2007-10-15
Why are you rewritting a program? You can not do what you seem to be attempting, most of the time, the program is already in Python, and a few core function are rewritten in C, which is possible, but I do not think you can do it the other way around.

---

### Post by cwaldbieser on 2007-10-15
> **aquavitae said:**
> I'm sure this is really simple, but I can't work it out.

I want to include a python interpretor in my c++ app.  How would I transfer data in the app to and from python scripts.  E.g. how would I write:
```

**c++:**
int a = 1;
int b = 2;
int c;
**to python:**
c = eval("a + b if a > 0 else 4", {'a' : a, 'b' : b})
*# or*
exec("c = a + b if a > 0 else 4", {'a' : a, 'b' : b, 'c' : c})

```

Not sure if that's clear... Help anyone?

Check out Boost python.  I found that to be pretty simple to use from C++.
[http://www.boost.org/libs/python/doc/]("http://www.boost.org/libs/python/doc/")

---

### Post by pmasiar on 2007-10-15
I think your program reached certain stage of maturity, so [Greenspun's tenth rule](http://en.wikipedia.org/wiki/Greenspun%27s_Tenth_Rule)  can be applied to it :-) [original source](http://philip.greenspun.com/research/)

If you need flexibility, do it other way around, like Alex martelli in Google does: "in Python, if we can get away with it, and C++ if we absolutely have to". I was trying to find the link, and **will** find it if it will help convert someone to Python :-)

---

### Post by cwaldbieser on 2007-10-15
> **LaRoza said:**
> Why are you rewritting a program? You can not do what you seem to be attempting, most of the time, the program is already in Python, and a few core function are rewritten in C, which is possible, but I do not think you can do it the other way around.

That is an odd thing to say.  There are a lot of applications that benefit from having a scripting language introduced to make them more flexible.  

On Windows, I can think of Internet Explorer, SQL Server 2000 DTS, Active Server Pages, and a raft of others.
On Linux platforms, Scribus comes to mind.

---

### Post by aquavitae on 2007-10-15
> **pmasiar said:**
> I think your program reached certain stage of maturity, so [Greenspun's tenth rule](http://en.wikipedia.org/wiki/Greenspun%27s_Tenth_Rule)  can be applied to it :-) [original source](http://philip.greenspun.com/research/)
Uhh... possibly... Don't worry, I'm already converted.  Unfortunately my code isn't.  Bits of it can be changed fairly easily, and that's what I'm trying to do, as well as add the possibility of scripting.
> Why are you rewritting a program? You can not do what you seem to be attempting, most of the time, the program is already in Python, and a few core function are rewritten in C, which is possible, but I do not think you can do it the other way around.It is possible, the docs make that clear, but I can't work out how.
> Check out Boost python. I found that to be pretty simple to use from C++.
[http://www.boost.org/libs/python/doc/](http://www.boost.org/libs/python/doc/)I did look at it a while ago, bit it didn't look that much use.  I'll have a look again now that I have a specific problem.

---

### Post by Soybean on 2007-10-15
When people embed Python in a C/C++ program, it's usually so that they can script the overall program flow in Python, while doing the "serious work" in a lower-level language. That is, it's essentially the same situation as writing the program in Python and rewriting the bottlenecks in C++, it's just approached from the other direction. Wanting to call a Python function from C++ is actually a little weird.

That said, I suspect it's possible. You'll just probably need to look at it from the other side until you understand the concept well enough to implement what you want. So, learn how to embed a Python interpreter in your C++ program for the purpose of calling C++ functions from Python (the more common and well-documented use-case), and along the way you should pick up the knowledge required to make it work the other way. You may want to look into something called "SWIG" for this.

---

### Post by aquavitae on 2007-10-16
> **cwaldbieser said:**
> Check out Boost python.  I found that to be pretty simple to use from C++.
[http://www.boost.org/libs/python/doc/]("http://www.boost.org/libs/python/doc/")
I'm had another look at it - it looks like exactly what I need, thanks.  Don't know how I missed it before!

---

### Post by aquavitae on 2007-10-16
I'm using boost.python, but I can't get it to compile:  I get the error ```
undefined reference to `_imp___Py_NoneStruct'
```I'm using qmake, and I'm linking to boost_python-mgw34-1_34.a.  I'm doing this on windows using mingw (they won't let me use linux at work - the bastards!)  The embedding example in boost compiled fine (although when I try to run it, it can't find the boost_python dll - I haven't really looked it)

Any suggestions?

---

### Post by JDahl on 2007-10-16
You probably already read this:
[http://docs.python.org/ext/embedding.html](http://docs.python.org/ext/embedding.html)

I use Python from both C and C++,  and I made a simple 
example documented here:
[http://abel.ee.ucla.edu/cvxopt/examples/miscellaneous/embed_cvxopt.c/view](http://abel.ee.ucla.edu/cvxopt/examples/miscellaneous/embed_cvxopt.c/view)

It uses a Python library CVXOPT so not everything is regular
Python,  but the example shows how to pass data to and from 
Python.

Joachim

---

### Post by aquavitae on 2007-10-16
Thanks for the reply.  Yes, I did read the python docs.  I can compile it without boost - I'm linking to the python libs, but I can't get boost to link properly.  I think that's why I gave up on boost.python before.

---

### Post by aquavitae on 2007-10-16
Nevermind - I found the problem.  I was trying to link against the static boost library but the dynamic python library.  Got it compiling now!

---

