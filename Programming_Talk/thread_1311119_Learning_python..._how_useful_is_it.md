---
title: "Learning python... how useful is it?"
date: 2009-11-02
forum: Programming Talk
---

### Post by emigrant on 2009-11-02
hi,
im in my early stages of learning python and am currently going with the book 'byteofpython'.

btw im wondering how far the language python would be useful and in which areas.
or is it worthless to learn python and should i focus on some other langs like c# or java?

also i would like to know, does learning python can contribute to my ubuntu/linux knowlegde?

thank you for your inputs...
:KS

---

### Post by giuspen on 2009-11-02
Your ubuntu/linux knowledge will increase for sure if you play with some python, especially if you start to play with pygtk too.
It will be probably less useful for finding job, as it's not much requested (at least not in Italy).

---

### Post by Reiger on 2009-11-02
There's always something. Be it an automated version of a tedious task or a GUI to a command line tool...

---

### Post by emigrant on 2009-11-02
i heard, google jobs look for python, though python is not that famous in my country too.

---

### Post by froggyswamp on 2009-11-02
It's very useful, very very, very very very useful, a lot. very very.
How about Googling first.

---

### Post by emigrant on 2009-11-02
> **froggyswamp said:**
> It's very useful, very very, very very very useful, a lot. very very.
How about Googling first.

my primary search engine: ubuntuforums.org
open a thread and enter the keywords...
:KS

---

### Post by unknownPoster on 2009-11-02
I work as a part-time student programmer for my university. Majority of what I've been tasked to do has been in PHP and Java. However, sometimes I get asked to do work on a time-critical project. When time of development and functionality are the highest concern, and I have the freedom to do so, I always use Python.

So, when my boss comes in and says, "We need a copy of every image on our website." I could just download every image manually, but that would take hours. Or I could spend an hour writing a Python script to do it for me. :)

---

### Post by 0cton on 2009-11-02
python is turing complete therefore pretty much everything you can do with java or C# you can do with python as well.

---

### Post by emigrant on 2009-11-02
in python can we design interfaces? or is it always 'command prompt'?

---

### Post by days_of_ruin on 2009-11-02
> **emigrant said:**
> in python can we design interfaces? or is it always 'command prompt'?

No, there are bindings for Gtk, Qt, WxWidgets and other graphical toolkits. A full list is here: [http://wiki.python.org/moin/GuiProgramming]("http://wiki.python.org/moin/GuiProgramming")

---

### Post by Can+~ on 2009-11-02
> **0cton said:**
> python is turing complete therefore pretty much everything you can do with java or C# you can do with python as well.

That's one weird argument. Even brainf*ck is turing complete.

> btw im wondering how far the language python would be useful and in which areas.
or is it worthless to learn python and should i focus on some other langs like c# or java?

No language is worthless, even if you don't use it professionally (unless you get a job on Google, or NASA), it will help you open your way to other languages, or paradigms, or even create quick prototypes.

And using it as "hacker" (not the Hollywood hacker (type fast = cool), [the real one]("http://catb.org/~esr/faqs/hacker-howto.html")) is where python shines. Use it in OSS projects, standalone useful applications, console utilities... the sky is the limit. It's way more "fun" than having to deal with the tight-*** OOP in Java/C# (at least for me, and most rational human beings).

> also i would like to know, does learning python can contribute to my ubuntu/linux knowlegde?

Most things on gnome and ubuntu have bindings for python. You'll frequently find a library on C that behaves exactly like one in Python (GL/GLU/GLUT for example). And also, python code takes a lot of inspiration from linux libraries, many names are pretty much identical to their C sys/<something>.h counterpart, minus pointers and all the boring stuff.

> **emigrant said:**
> in python can we design interfaces? or is it always 'command prompt'?

As days_of_ruin pointed out, there are various bindings for toolkits. My first one was GTK+, but after seeing QT4 recently, I think I started the wrong way. QT4 seems to be "better abstracted" than GTK+ in many ways.

---

### Post by grayrainbow on 2009-11-02
> That's one weird argument. Even brainf*ck is turing complete.
[http://en.wikipedia.org/wiki/Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) it's even more - it's brainfuck :) but I really like it(as an idea of esoteric language).

Usually I seen python be used in places where in the past people used perl, mainly for automation of administrative tasks. There's one really bad thing in python - it offer nothing new to the programmer, and just look like(and actually is) remix of other programming languages. There's also one really good thing about python - it's just trivial to extend it with library written by you, and that's put it in the realm of extreamly useful toy languages(toy language - script that one could use for test how something work, let say OpenCL), much better than java/C#.

Compared to C# or java...well, with python you want get even near the IDEs functionality which this languages have. There's no copy of C++ tamplates, java and C# have such copy. There's no delegates like in C#(extreamly useful, especially with templates), python lambda is a joke.

P.S. Experience programmer can do simple things fast regadless of the language in use, after all usually the speed up comes from the libraries not from the language(assuming programmer knows what he/she is doing, and not counting some "dirty" C tricks).

---

### Post by Bodsda on 2009-11-02
> **grayrainbow said:**
> 
Usually I seen python be used in places where in the past people used perl, mainly for automation of administrative tasks. There's one really bad thing in python - it offer nothing new to the programmer, and just look like(and actually is) remix of other programming languages. 

I use python for one liners, automation, applications, graphical development. It is not limited to automation and there are many many more substantial uses for python. Pygame for example. 

And python being a remix and look alike of other languages... I can't think of many other languages that look like python. As for the mix up, PHP is more of a type of language that tried to grab the best bits from a few others and mash them together.

---

### Post by Can+~ on 2009-11-02
> **grayrainbow said:**
> Compared to C# or java...well, with python you want get even near the IDEs functionality which this languages have. T**here's no copy of C++ tamplates**

Why would you need templates when everything is dynamically typed?

> **grayrainbow said:**
> There's no delegates like in C#(extreamly useful, especially with templates)

Why, when there is duck typing and dynamically typed (again)?

> **grayrainbow said:**
> python lambda is a joke.

Lambdas behave exactly as expected in a functional language. If you don't like it, you can plug a regular function.

---

### Post by unknownPoster on 2009-11-02
As Bodsda said, PyGame is a useful wrapper to SDL. I find it much easier and straightforward to use than C/C++ with SDL.

---

### Post by nvteighen on 2009-11-02
> **emigrant said:**
> hi,
im in my early stages of learning python and am currently going with the book 'byteofpython'.

btw im wondering how far the language python would be useful and in which areas.
or is it worthless to learn python and should i focus on some other langs like c# or java?

also i would like to know, does learning python can contribute to my ubuntu/linux knowlegde?

thank you for your inputs...
:KS

Python is very useful because it's a language that allows you to forget a lot of internal machinery stuff that's only relevant when you need to optimize your code for critical speed and in some other niches. It brings very well-thought basic data structures and a great set of standard modules that make the language really powerful from the beginning. That, plus the amount of third-party modules you have out there, makes the language really worth.

Of course, after learning Python you should learn other languages. I'd recommend you to rather look at C than Java or C#.

> **emigrant said:**
> in python can we design interfaces? or is it always 'command prompt'?

Interfaces... A procedure has an interface. A data structure has an interface. You mean User Interfaces and possibly, Graphical User Interfaces (GUI)... :P

Yes, you can: as other have said, you can use PyGTK+ (GNOME-friendly), PyQt (KDE-friendly), wxWidgets (a third possibility).

> **grayrainbow said:**
> 
..., python lambda is a joke.


> **Can+~ said:**
> 
Lambdas behave exactly as expected in a functional language. If you don't like it, you can plug a regular function.

Nope, sadly, Python lambdas are a joke because of their arbitrary one-line restriction and the prohibition of using assignment inside them. Ok, about the second, one could argue Python lambda's are pure-functional... but the issue is that the whole language is very imperative-based and that decision is completely weird with respect to the Python semantical system. Common Lisp and Scheme don't place that restriction and allow any valid procedure code to be enclosed in a lambda, not a subset of valid procedure code.

I've always felt Python functional features are sad and badly designed afterthoughts, except maybe for list comprehensions.

---

### Post by rich1939 on 2009-11-02
> **giuspen said:**
> Your ubuntu/linux knowledge will increase for sure if you play with some python, especially if you start to play with pygtk too.

I had a lot of trouble getting pygtk to run on windows; whereas, I had no trouble getting pyqt to work just fine.

I am familiar with GTK+ and am using it with C and Glade on Ubuntu...but have not had very good luck on windows.

I'm learing Python and had the same difficulties integrating it with GTK+. I had no trouble integrating Python with Qt, using pyqt and QT Designer.

Just a thought that learning QT and Python together might be a good way to go.

---

### Post by Can+~ on 2009-11-02
> **nvteighen said:**
> I've always felt Python functional features are sad and badly designed afterthoughts, except maybe for list comprehensions.

Guido mentioned (in 2005) that the idea is to remove pretty much all higher-order functions in Py3:

[http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

(In fact, reduce has been moved to the functools).

I feel that lambda is there just for easy short anonymous functions, more than anything. If it goes away, I wouldn't mind either.

---

### Post by benj1 on 2009-11-02
> **Can+~ said:**
> Guido mentioned (in 2005) that the idea is to remove pretty much all higher-order functions in Py3:

[http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

(In fact, reduce has been moved to the functools).

I feel that lambda is there just for easy short anonymous functions, more than anything. If it goes away, I wouldn't mind either.

dont scare me like that ;)
i dont know how i would live without map.

lambda im not too worried about, most uses i had for it have gone now that ive found 'if *boolean* and foo or bar'. plus functions are so easy to write for most purposes

---

### Post by A_Fiachra on 2009-11-02
> **0cton said:**
> python is turing complete therefore pretty much everything you can do with java or C# you can do with python as well.


xslt is Turing-Complete.

Not a good argument for adopting one programming language over another.


Python has several benefits:

1) it is a general purpose programming language that supports OO

2) it has "batteries included" -- there are thousands of classes in the standard distribution that will probably get the job done.

3) its popularity is on the rise.

4) it has become the default language for several popular Linux utilities -- e.g. Yum

5) it is actually open source, unlike Java which is owned by Sun or C# which is owned by microsoft

6) it is executable pseudo-code, that is, it is relatively easy to learn the syntax, easy to maintain code, transparent across OS's and repositories, it avoids idiosyncrasies that can make Perl almost unusable at times, even the worst Python coder can't **** up so much that you can't refactor code.  

7) Avoids the miasma of Java -- which has 9,000 versions, a dozen compilers, a few thousand incompatible versions and the bondage and discipline attitude of forcing everything to be class or interface


I get a lot of work with Python and it tends to be new development.

---

### Post by ahmatti on 2009-11-03
Python is very useful :) Have a look at the sticky thread for links and info [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by CptPicard on 2009-11-03
Now that I think of it, the one-line python lambda is essentially an expression that has a value (possibly) dependent on the lexical scope, although it is an expression you can comfortably "pass around".

I really hope Python doesn't get too dumbed down down the functional-removal road -- the functional stuff is very useful in "advanced Python"...

---

### Post by nvteighen on 2009-11-03
> **CptPicard said:**
> Now that I think of it, the one-line python lambda is essentially an expression that has a value (possibly) dependent on the lexical scope, although it is an expression you can comfortably "pass around".

I really hope Python doesn't get too dumbed down down the functional-removal road -- the functional stuff is very useful in "advanced Python"...

Hm... I'm not sure... I've always felt nested functions as much more useful than the one-liner lambda... The Python lambda usage is almost restricted to provide the predicate for map, filter and reduce.

I wouldn't like to see Python lose its functional features, even though I think they're just an afterthought and a peripherical set of functions. Some of us use them, maybe because of Lisp-influence, and to lose them would affect my way of coding in Python. Nevertheless, those are still weird additions with respect to the whole Python language.

---

### Post by samjh on 2009-11-03
> **emigrant said:**
> i heard, google jobs look for python, though python is not that famous in my country too.

Not much Python in Australia either.

Google doesn't seem to ask for Python much.  They seem more interested in C++ and Java.  Python and Perl are sometimes listed as advantages.

---

### Post by matthew.ball on 2009-11-04
Just had a guy (ex-graduate) from google in Sydney, drop in to our university and give a guest lecture..

From what I remember they were massively into Python and C++ (with emphasis on the latter for low-level stuff, like gfs, and all their concurrency, and the former for high-level development). It was a concurrency-related lecture, so we were more focused on the low-level stuff, he just mentioned Python briefly.

That said, if you're learning a language purely for a job, you're doing it wrong.
*Especially* a cross-paradigm language like Python. I really think this is an all too understated power of Python, it moulds everything nicely together.
Learn the concepts not the syntax - you'll be able to transfer the knowledge across domains. If you've learnt by syntax, yes you can transfer "majority" of what you know, but learning anything new will be more difficult (it will always be in terms of what you know).

---

### Post by CptPicard on 2009-11-04
> **matthew.ball said:**
> It was a concurrency-related lecture, so we were more focused on the low-level stuff, he just mentioned Python briefly.

It should be noted though that a very important idea these days in parallelism and concurrency is getting rid of shared mutable state altogether (pure-functionality) or isolating it somehow (Clojure). Concurrency becomes much easier if you're able to side-step the causes causing the problem in the first place.

> 
*Especially* a cross-paradigm language like Python. I really think this is an all too understated power of Python, it moulds everything nicely together.
Learn the concepts not the syntax - you'll be able to transfer the knowledge across domains. If you've learnt by syntax, yes you can transfer "majority" of what you know, but learning anything new will be more difficult (it will always be in terms of what you know).

QFT. This is what I've been ranting about here for years, to varying degrees of success... :) One really is not a fully grown programmer before one is able to transcend syntax and be able to think in terms of the language's concepts... how they relate to the problem, and how they relate to perhaps other concepts in other languages. After all, they're all Turing-complete, so there is a way to emulate a language idea in some other language. Python is nice, in particular for a beginner but for more advanced programmers too, in its nice design which combines economically and orthogonally a lot of nice ideas and actually makes them also work together well...

---

### Post by Reiger on 2009-11-04
> **nvteighen said:**
> Hm... I'm not sure... I've always felt nested functions as much more useful than the one-liner lambda... The Python lambda usage is almost restricted to provide the predicate for map, filter and reduce.

I wouldn't like to see Python lose its functional features, even though I think they're just an afterthought and a peripherical set of functions. Some of us use them, maybe because of Lisp-influence, and to lose them would affect my way of coding in Python. Nevertheless, those are still weird additions with respect to the whole Python language.

Although the inner function can be used as lambda-style argument:
```

>>> def factorial(arg):
...   def recurse(n,v):
...       if n == 1:
...          return v
...       else:
...          return recurse(n-1, n*v)
...
...   return recurse(arg, 1)
>>> factorial(5)
120
>>> factorial(3)
6

```

And you could wrap that in a lambda like so:
```

(lamba arg: return recursive_func(arg))

```

---

