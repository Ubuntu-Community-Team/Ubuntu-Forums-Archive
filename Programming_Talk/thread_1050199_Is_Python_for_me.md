---
title: "Is Python for me?"
date: 2009-01-25
forum: Programming Talk
---

### Post by COMTIBoy on 2009-01-25
Hi Everyone,

I come from a Windows background (C++, assembly, ATL, and .NET ) and brand spanking new to Linux. 

As a way to get acclimated to the whole Linux environment, I decided to write a program that will give me experience with GUI development and database access to Db2.  I want to write a simple program that presents a nice GUI (simulating a bank teller machine), does a query to DB2, then presents the return data in a nicely formatted grid.  Afterwards, I want to change the program to make use of a web service which essentially does the work and returns the data back to my gui program to be displayed in a grid. 

I decided that I'm going write a C++ program in QT4 as I think this would present a lesser learning curve for me; however; a friend of mine suggested that I hunker down and learn Python.

I've never used Python but wanted to get some feedback from more experienced folks, if this is the way to go.  The whole point of me using Linux is simply to learn and try things that I'm completely unfamiliar with...and adding Python would definitely be contributing to my new experience factor. 

So, is this something easy to do in Python ?  Does Python have any grid widgets ( controls ).

Thanks in advance for your feedback.

---

### Post by CptPicard on 2009-01-25
I believe you've hit the nail on the head regarding why you should try Python... it gives you a slightly different view on things. You already know C++ so there would not be that much new stuff for you to learn if you did not branch out.

Python has both Qt and GTK bindings, and I hear that Qt programming in Python is quite pleasant (I don't really do GUIs myself so I can't comment from personal experience). Your kind of quick db app sounds like a perfect fit for Python.

There's also the added benefit that Python's learning curve is not steep, so you can quickly jump on board, but in the long run the language is deeper than what first meets the eye.

---

### Post by Kilon on 2009-01-25
> **COMTIBoy said:**
> Hi Everyone,
The whole point of me using Linux is simply to learn and try things that I'm completely unfamiliar with...

new things , completely unfamiliar with ? hmmm bad choice ... move away from python. 

with python you will see that that is exactly the type of product that is made to be felt as natural as speaking.

---

### Post by brentoboy on 2009-01-26
Python is a fun language (I speak C++, assembly, .net, and a little ATL).  I would definitely play with it.  But you will probably want to start off with command line apps.

I find python a breath of fresh air.  Its object oriented, but not as strict as C++.   You need to at least skim the Dive Into Python book (can be found online for free).

The only only learning curve I found is that variables are significantly different.  Vectors, Strings and Associative arrays are built in types, and functions can return multiple values like this:
x, y = getCoords()

Playing with python was the first "fun" I have had programming in almost 6 years.  Its the first time in a long time that I have looked at a completed project and said "neat" instead of saying "look, it works"

When you want to make the jump from command line to graphical user interface, use wxPython, it is a python wrapper for the wxWidgets toolkit designed to use native widgets on several operating systems, so your app will look like a windows app if you run int on windows, it will use QT if you use KDE, and it will use gdk if you run it on the Gnome desktop.

Also, much of the code belonging to the Ubuntu Project is written in Python, so by learning python you will be in a position to contribute to the project if you bump into something you are interested in.

---

### Post by nvteighen on 2009-01-26
"Is Python for me?"

That's a philosophical question you'll only be able to answer if you try it ;)

Man, this is not *that* important. If you don't like it, you leave it there and you won't die!

---

### Post by Kilon on 2009-01-26
You will find tons , of info , literally tons of information why you should choose python. It is everywhere, the evidence is pretty over whelming. 

One deep Look on why python rock can be found here , it is a blog justifying the jump to python 3 which brakes compatibility with previous python  versions but also gives alot of reasons why python is the most commonly suggested solution to a problem. 

[http://www.b-list.org/weblog/2008/dec/05/python-3000/](http://www.b-list.org/weblog/2008/dec/05/python-3000/)

---

### Post by stevescripts on 2009-01-26
Python would be a fine language for you to explore, and there are, of course, other higher-level languages to explore. (Tcl, Ruby, Lua ...)

As for reasoning on moving away from compiled programming to higher-level languages, this is always good reading:

[http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

---

