---
title: "Why Python?"
date: 2008-08-31
forum: Programming Talk
---

### Post by PaulM1985 on 2008-08-31
Hi All

I know Java fairly well and I know a little bit of C.  I try to come on to here to ask questions and help out when I can.  I have noticed that the majority of questions are about Python, something I know nothing about.

The main question is:
Why Python?

What are the advantages/disadvantages of Python?
Is it Windows compatible?
Can you create GUI?
etc

As the majority of questions on here are about Python, I thought maybe it would be worth learning due to its popularity.  And maybe I could eventually help someone with it.

Paul

---

### Post by leg on 2008-08-31
Python is fairly similar to Java in that it is interpreted. It is becoming a very popular language due largely to the fact that it is very easily embedded as scripting language. Blender, for instance, uses it for scripting. Yes Python is more than capable of GUIs and has a library for them. I myself have not done much Python except for a few experiments in Blender. 

Yes it is compatible with Windows in the same way as Java is. As long as the interpretor is installed you can run Python programs. One thing I really liked about Python is the fact that indents are part of the syntax and so forces cleaner code.

Have a look and see what you think. [http://www.python.org/]("http://www.python.org/")

---

### Post by cmay on 2008-08-31
i dont use python. i have bad eyes so it would be impossible for me to learn. but there is one great advantage in the license. its free and in a way where it is possible to embed it in commercial products whit out having to show the source. at least it was that license terms i read in a read me file on redhat 6.0. maybe that has changed later. for clarity about that you will have to ask some one that knows for sure.

---

### Post by realitybites on 2008-08-31
i am new to python, but i have good experience with c++,c#,php and even scheme so i can say python is the easiest among all of them. i mean very very easy. you can do whatever you want with a little amount of code. now i wanna do everything with python

my first application with python had a gui. there are a few good gui libraries (python bindings for gtk, qt, etc.)

---

### Post by rogeriopvl on 2008-08-31
Python is perfect for rapid application development. You can make fairly complex applications in no time and with very few lines of code.

I've started with Python only recently. During 6 years I only used languages like Java and C and some Haskell, and I tell you, Python is the best thing that happened in programming.

You can find more information everywhere, google, python.org etc.. Give it a try, you won't regret and you'll learn the syntax in minutes ;)

---

### Post by nvteighen on 2008-08-31
Well, it's a quite simple high-level language that allows you to do things more easily and straight to the point, without caring for memory management (as you code in C, you know what a pain that is) and other boilerplate code.

But it's nicest feature is its interactive prompt, no doubt.

---

### Post by Wybiral on 2008-08-31
One plus about Python is that it's [dynamically typed]("http://en.wikipedia.org/wiki/Type_system#Dynamic_typing") (which makes rapid, generic development easier). It has pseudocode-looking, clean sourcecode (none of the weird semi-colons and brackets you get in other languages). It has support for object oriented and procedural design, but also decent support for [functional programming]("http://en.wikipedia.org/wiki/Functional_programming"). Native support for commonly used datatypes such as vectors (lists), sets, and hashmaps (dicts).

It has a [huge (and well-written) standard library]("http://docs.python.org/lib/"), with the motto "batteries included" (to the extent of "import everything" being a joke... [xkcd.com/353]("http://xkcd.com/353/") and [xkcd.com/413]("http://xkcd.com/413/"))

Some excellent web frameworks such as [TurboGears]("http://turbogears.org/") and [Django]("http://www.djangoproject.com/") (as well as great, scalable, free hosting on [Google App Engine]("http://code.google.com/appengine/")).

It's also very easily extendable with C or C++ using something like [CTypes]("http://docs.python.org/lib/module-ctypes.html"), [SWIG]("http://www.swig.org/"), or [PyRex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/"), in case you need to add support for a low-level library or speed up a bottleneck in your code (which there is also [psyco]("http://psyco.sourceforge.net/"), a JIT compiler module).

To sum it up, it's definitely a language worth learning :)

---

### Post by CptPicard on 2008-08-31
> **leg said:**
> Python is fairly similar to Java in that it is interpreted.

Actually, both are bytecode-compiled, not strictly "interpreted"... :)

---

### Post by pmasiar on 2008-08-31
Read 'Why I love/hate Java' and 'Why...Python' threads in stickies, we discussed this issue many times.

Short summary: Python, compared with Java, has couple 'killer' features (this is from someone who struggles with  Java in day job):

- dynamic typing simplifies library a lot. You don;t have to research library to find matching class all the time: why Java needs 60+ file-like classes?
- Python library and syntax fits in my limited brain much better than Java (and I have 20+ years of programming experience, I am not a noob)
- dynamic (non-checked) exception simplify creating pilot project: just ignore exceptions, handle them when they crash, but dig deeper into your problem
- shell allows you to create and interrogate object in commandline, instead of writing simple programs to just instantiate and test project methods
- flexible data structures and literals: it's trivial to create HashMap (dictionary) and populate it with couple elements in single line of code.
- clear, concise code: Python takes about 1/3 of the lines of similar Java code, 1/5 of the time to write it, and 1/2 time to debug it.

---

### Post by PaulM1985 on 2008-08-31
Thanks everyone for all your input.  I think this is something I will look into when I have a bit of spare time.  My uni work is heavily Java focused, so I will learn this when uni quietens down.

One last question (without going into the .exe Java argument that has been going on), does it compile in Windows with a .exe extension, or does it need a runtime environment or something similar.

Thanks again for all the comments.

Paul

---

### Post by crazyfuturamanoob on 2008-08-31
> **PaulM1985 said:**
> Thanks everyone for all your input.  I think this is something I will look into when I have a bit of spare time.  My uni work is heavily Java focused, so I will learn this when uni quietens down.

One last question (without going into the .exe Java argument that has been going on), does it compile in Windows with a .exe extension, or does it need a runtime environment or something similar.

Thanks again for all the comments.

Paul
Just as he said in another topic:
> **Yannick Le Saint kyncani said:**
> You don't need to compile it, python programs are interpreted at run-time.

---

### Post by leg on 2008-08-31
> **CptPicard said:**
> Actually, both are bytecode-compiled, not strictly "interpreted"... :)True.

---

### Post by LaRoza on 2008-08-31
> **PaulM1985 said:**
> 
One last question (without going into the .exe Java argument that has been going on), does it compile in Windows with a .exe extension, or does it need a runtime environment or something similar.


It is like Java in that respect. ActivePython is a Python installer and most libraries work the same way, so it is simple to have (just like you need a JRE to use Java). HP and Compaq computers, OS X and most Linux distros come with Python.

One can "compile" it, with py2exe or "freeze" so you can distribute it anywhere.

---

### Post by pmasiar on 2008-08-31
You can distribute .pyc files instead of .py sources, but it's not hard to restore source code from them (minus comments of course), but hardly anybody does it. And exactly like .NET or Java, you need to install runtime environment - which is the same as compile environment :-)

On Windows, use ActiveState Python installer, it just works (including environment setting).

---

### Post by LaRoza on 2008-08-31
> **pmasiar said:**
> 
On Windows, use ActiveState Python installer, it just works (including environment setting).
And for GUI Python apps, make the extension ".pyw" so it won't open a terminal.

---

### Post by PaulM1985 on 2008-09-01
Thanks again everyone.  Learn Python is obviously something to put on my to do list

---

