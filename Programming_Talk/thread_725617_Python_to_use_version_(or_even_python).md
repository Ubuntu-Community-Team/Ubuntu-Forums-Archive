---
title: "Python to use version? (or even python?)"
date: 2008-03-15
forum: Programming Talk
---

### Post by Soleil-Raid on 2008-03-15
Howdy,

I'm looking at developing an application that manages a bunch of already written apps. Because I expect (hope!) this eventually to become quite large, I'm trying to sit down and work things out before I just start hacking away at code.

I eventually decided on Python, because it already has support for all of the modules I will need, seems to be a very clean language from the little bit I've done, and works well in all three environments (Web, CLI, GUI), and the application is expected to eventually cross all three.

However, I understand that python is in a transition period from 2.4 to 2.6/3.0. Is this likely to be a problem?

I'd expect it to be at least six months before an alpha of v1.0 of this application is ready.

Due to my lack of experience with it, I'm not entirely sure python is the right tool for the job. Most/all of the heavy lifting will be done by various already-implemented C backends. Principally, I need a OSS language that's happy in all three areas, and isn't too 'heavy', and has good support for Kerberos, LDAP, XML, and strings.

Any comments/thoughts?

---

### Post by LaRoza on 2008-03-15
Python 3000 will be have some differences which won't be backwards compatible, however, 2.5 will be around for a while, and there are ways of automating the switch.

The differences are relatively minor, like the removal of raw_input() and making it inpu() and the current input() will need to be expressed as eval(input()). 

You can use 2.5 safely, and it won't be a big thing when Python 3000 comes out.

---

### Post by pmasiar on 2008-03-15
Py2.6 will have special mode which will warn about suspicious syntax. And there will be 2.6to3.0 converter, so you can write correct 2.6 code which will be converted to correct 3.0 code automagically.

To be even more sure, you can (should anyway) write bunch of test. If your converted 3.0 code passes the same test as your 2.6 code, you are all set.

There also will be Python 2.7, possibly 2.8 and 2.9, so you can switch when ready. For sure there will be no Python 2.10 - as Guido said "it does not sort right" :-)

---

### Post by amingv on 2008-03-15
Also FAQ 2.5 (The version number, coincidence? :)):

> 2.5   Is it reasonable to propose incompatible changes to Python?

In general, no. There are already millions of lines of Python code around the world, so any change in the language that invalidates more than a very small fraction of existing programs has to be frowned upon. Even if you can provide a conversion program, there still is the problem of updating all documentation; many books have been written about Python, and we don't want to invalidate them all at a single stroke.

Providing a gradual upgrade path is necessary if a feature has to be changed. PEP 5 describes the procedure followed for introducing backward-incompatible changes while minimizing disruption for users.


Gradual update path; you should be OK.

---

