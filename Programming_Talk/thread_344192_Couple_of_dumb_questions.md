---
title: "Couple of dumb questions"
date: 2007-01-22
forum: Programming Talk
---

### Post by Rich78 on 2007-01-22
I have a couple of dumb questions being a Windows developer.

I would like to start developing on the Linux platform but for my first project I actually want to develop an application for my PDA which is based on Familiar running GPE.

I have looked at the GPE site for tips but it's in C++ which isn't a problem but even the most basic helloworld app seems OTT and doesn't make the best of sense when it comes to needing various bits such as GTK and then having a weird configure file to run before you can compile etc.

I was wondering if I was to develop in Python could it run on the GPE environment, as GPE is essentially Gnome?

Also when I wrote a small helloworld Python app, I have the .py extension which is fine if I want to run Python helloworld.py, but how do I go about compiling/packaging it etc?

Thanks and sorry if these questions are a bit dumb but the info seems hard to find, or I'm looking in the wrong places.

---

### Post by Grey on 2007-01-22
I know nothing of this subject.  I don't personally use automake for my stuff, and I do not own or use a PDA.

But it sounds like GPE is using automake.  Which is probably a good thing, although you don't know it yet.  It makes it really nice and easy to compile your program.  It's a lot like a command line version of an IDE.  You will find that a lot of linux software ships in source code form, and uses automake to actually build and install the software.  I would advise just following the advice that the GPE site is giving you.

And as far as Python goes... Python is not a compiled language.  It's an interpreted language.  So if you have a python interpreter and pygtk on your PDA, then you are probably good to go.  Save your file as something.py, and then run it on the PDA.

---

