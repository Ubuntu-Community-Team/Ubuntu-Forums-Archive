---
title: "Python 2 or 3"
date: 2013-01-20
forum: Programming Talk
---

### Post by AgentZ86 on 2013-01-20
Hi all

I started learning python a while back and it was said that libraries would be better for 2.6 / 2.7 at that time

But it's been some time now and want to resume my learning on python.

Soooooo should I resume learning 2 or 3 ?
What will be best and where will most of the currently libraries be available ? 

Please advise
Thanks

---

### Post by greg_ory on 2013-01-20
Python 2.0 was released on 16 October 2000
Python 3.0 was released on 3 December 2008

Well, I would go for 3.0 but not sure if you have an old codebase what you need to migrate.

-Greg

---

### Post by NilPointer on 2013-01-20
Python 2 has tons of libraries (much more than was ported to or created for Python 3).

Python 3 is enhanced a bit, but is not backwards-compatible. It has some advantages. For example, it uses unicode strings, and if you have to deal with different encodings and non-ASCII symbols, it may seem much simpler (in Python 2 you need to explicitly decode strings from 8-bit to unicode and encode from unicode to 8-bit, and unless you figured out how it works, you may get bunch of UnicodeErrors, Python 3 in most cases does that for you).

I prefer Python 2. Working with encodings is not that hard, and there are ready libraries for all needs.

P.S. And yes, Python 2 is still getting updates (and even backports of some goods from 3.x). Current version is 2.7.3 and 2.7.4 is coming soon.

---

### Post by greg_ory on 2013-01-20
> **NilPointer said:**
> Python 2 has tons of libraries (much more than was ported to or created for Python 3).

Python 3 is enhanced a bit, but is not backwards-compatible. It has some advantages. For example, it uses unicode strings, and if you have to deal with different encodings and non-ASCII symbols, it may seem much simpler (in Python 2 you need to explicitly decode strings from 8-bit to unicode and encode from unicode to 8-bit, and unless you figured out how it works, you may get bunch of UnicodeErrors, Python 3 in most cases does that for you).

I prefer Python 2. Working with encodings is not that hard, and there are ready libraries for all needs.

Compatibility and Transition

Python 3.0 will break backwards compatibility with Python 2.x.

There is no requirement that Python 2.6 code will run unmodified on Python 3.0. Not even a subset. (Of course there will be a tiny subset, but it will be missing major functionality.)

Python 2.6 will support forward compatibility in the following two ways:

    It will support a "Py3k warnings mode" which will warn dynamically (i.e. at runtime) about features that will stop working in Python 3.0, e.g. assuming that range() returns a list.
    It will contain backported versions of many Py3k features, either enabled through __future__ statements or simply by allowing old and new syntax to be used side-by-side (if the new syntax would be a syntax error in 2.x).

Instead, and complementary to the forward compatibility features in 2.6, there will be a separate source code conversion tool [1]. This tool can do a context-free source-to-source translation. For example, it can translate apply(f, args) into f(*args). However, the tool cannot do data flow analysis or type inferencing, so it simply assumes that apply in this example refers to the old built-in function.

The recommended development model for a project that needs to support Python 2.6 and 3.0 simultaneously is as follows:

    You should have excellent unit tests with close to full coverage.
    Port your project to Python 2.6.
    Turn on the Py3k warnings mode.
    Test and edit until no warnings remain.
    Use the 2to3 tool to convert this source code to 3.0 syntax. Do not manually edit the output!
    Test the converted source code under 3.0.
    If problems are found, make corrections to the 2.6 version of the source code and go back to step 3.
    When it's time to release, release separate 2.6 and 3.0 tarballs (or whatever archive form you use for releases).

It is recommended not to edit the 3.0 source code until you are ready to reduce 2.6 support to pure maintenance (i.e. the moment when you would normally move the 2.6 code to a maintenance branch anyway).


Source:
[http://www.python.org/dev/peps/pep-3000/](http://www.python.org/dev/peps/pep-3000/)

-Greg

---

### Post by Cheesehead on 2013-01-20
> **AgentZ86 said:**
> Soooooo should I resume learning 2 or 3 ?

Both. They are about 95% similar. A few syntactical differences, a few different libraries.
It's pretty easy to make most scripts compatible with both.

Ubuntu has a near-term goal of switching the default Python install from 2.7 to 3.x. According to the tracker at [http://people.canonical.com/~ubuntu-archive/transitions/onlypy3oncd.html](http://people.canonical.com/~ubuntu-archive/transitions/onlypy3oncd.html) , the change seems likely to happen in the 13.10 cycle.

---

### Post by AgentZ86 on 2013-01-20
This is a lot of information to consider

Since I'm sort of a noobish coder, and python is my first language most of my projects will be for personal use and run on my own server etc. 
But if there are way more libraries in 2.6 or 2.7 then this sounds like the way to go still but still hard to decide.

I mean if I code something in python 3 and package it up for someone to download it for use on a PC or something, then what ? 
Won't it be useable to anyone ? Or do they have to have the proper python in stalled ? 

AND If they need the proper python installed then I'm curious what most OS's are using now ? Mac,Linux,Windows 7, Windows 8 ?
That might help me decide as well if that even matters at all which python the end user needs to have installed ? 

If anyone can help clarify this some more that would be great

Thanks to everyone for the responses

---

### Post by Cheesehead on 2013-01-20
If you plan on distributing in the wild, then your script should run checks at startup to ensure it's in an appropriate python environment, has access to the libraries it needs, and gracefully fails and tells the user if some dependency is not installed.

If you plan on distributing by packages, then the package manager will ensure the dependencies you need are installed. You need merely specify the dependencies in the debian control file. In this case, 'dependency' includes the python version.

---

### Post by AgentZ86 on 2013-01-22
I see thanks

---

### Post by llanitedave on 2013-01-22
Numpy supports Python 3.  Matplotlib supports Python 3.  WxPython and Django are right on the verge of supporting it.

The latter two are what had me sticking with Python 2.7 for the last couple of years.  When they switch, I'll switch.  I'm actually looking forward to it.

---

### Post by lykwydchykyn on 2013-01-22
You can look at this two ways:

- If you learn python 2, you may have access to some great libraries that are stuck on version 2, which will end up leaving you stuck on version 2 until those libraries upgrade or get replaced.

- If you learn python 3, you may not have access to every library under the sun at first, but you won't have to relearn things and make painful transistions later.

I've been waiting and waiting and waiting on some projects to update to 3, or for python 3-compatible libraries to get the functionality I had it two.  It's a miserable wait.  If you don't have code with established dependencies, why burden yourself?

---

### Post by AgentZ86 on 2013-01-26
well I think I'll keep toying with python 2 for now since I'm a hobbiest anyhow

My project will likely be easy to re-write if I have to in pyhon 3 at some point or I could re-write the library I need to make it work I guess if i have to.

Back to the drawingboard

Happy hacking and thanks this has been helpful.

---

### Post by danniel on 2013-01-31
I notice that more and more projects begin to have support for Python 3.2+ **besides** Python 2.7, the most recent example being the Django Framework. 

So you should work with Python 2.7 for now, but write code which is mostly Python 3 ready by following the advice from here: [http://docs.python.org/2.7/howto/pyporting.html](http://docs.python.org/2.7/howto/pyporting.html) so that you can easily move to Python 3.3 sometime next year (just my estimation :D).


Also, never bother with Python 3.0 and Python 3.1, because they were only for testing purposes anyway. Also Python 2.5 and 2.4 are just too old.

---

