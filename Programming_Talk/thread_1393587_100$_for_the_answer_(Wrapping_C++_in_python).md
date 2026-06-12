---
title: "100$ for the answer (Wrapping C++ in python)"
date: 2010-01-29
forum: Programming Talk
---

### Post by bigdidz on 2010-01-29
Hello everyone!

I did a program in python.  The program is starting to be big; around 5000 lines of code.

The problem is the program need to be (very) fast.  At first, I did it in python to have the possibility to easily optimize the algo.

Now, 95% of the prossesing time is stock in one object.  I already wrote the major part of that object in C++.  Now I want to embedded my C++ object in my python code.

I googlize a lot and try out a multiple thinks. I know it is possible but presently, nothing works!  I was not even able to run the 'hello world' example of boost.python.

I just saw that cython can wrap c++ code.  But I cannot find a complete example (that compile on my laptop).  Actully, I would like to use Cython if possible.  But, whit no information, I'm stuck!

So I'm asking the entire planet help!! I don't want to rewrite my entire program in C++...  Does somebody have a comprehensive tutorial on how to wrap c++ using Cython?  An (complete and compilable) example would be great too.

If you know a good book that talk about it, I'm running at my bookstore to get it.

Thanks in advance,

Didier A.

P.-S.: The tutorial must be comprehensible for a dum mathematician like me...

---

### Post by SledgeHammer_999 on 2010-01-29
I think this will help-->[http://docs.python.org/extending/extending.html](http://docs.python.org/extending/extending.html)

---

### Post by CptPicard on 2010-01-29
SWIG, or Boost.Python.

How do I get my $100?

---

### Post by bigdidz on 2010-01-29
The problem with boost is the (major) lack of comprehensible documentation.  I'm a mathematician who wants to link a C++ object with a python program.

The best thing would be documentation from a university or something like it and a good example.  The boost Hello world doesn't work on Ubuntu.  I haven't try it on mac osX (the other O.S. I use at the university) but since two days... I came to a death end.


Thanks (Continue to reply)

D.A.

---

### Post by CptPicard on 2010-01-29
Well, sorry, welcome to the FOSS world... ;) Boost is actually relatively well documented, it just takes a somewhat experienced programmer to understand the documentation :)

---

### Post by casevh on 2010-01-29
Does the following link (which appeared on the Cython mailing list) help?

[http://wiki.cython.org/gsoc09/daniloaf/progress](http://wiki.cython.org/gsoc09/daniloaf/progress)

---

### Post by bigdidz on 2010-01-29
Seem interesting (actually the best).  I will try it later and I will gives you news.

Thanks

D.A.

---

### Post by TheStatsMan on 2010-01-29
> **CptPicard said:**
>  Boost is actually relatively well documented

I'm not so sure, Boost Python is notoriously badly documented.
Have a look at SWIG, it is pretty easy most of the time to wrap c++ classes. [http://www.swig.org/Doc1.3/Python.html#Python_nn13](http://www.swig.org/Doc1.3/Python.html#Python_nn13)

I have found for numerical work that for most cases Fortran is a better choice than C++ or C to choose when extending Python, even though I choose C++ over Fortran if I am restricted to the one language. You don't really need to do anything. Just compile your fortran code with f2py and then use it straight from Python. Much of what is annoying about fortran is lost when using it in combination with Python as well. It is also simpler than C and has higher level array functions built into the language, yet still is at least as fast as C.

---

