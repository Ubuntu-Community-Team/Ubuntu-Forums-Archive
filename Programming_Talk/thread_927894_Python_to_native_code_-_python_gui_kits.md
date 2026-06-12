---
title: "Python to native code - python gui kits"
date: 2008-09-23
forum: Programming Talk
---

### Post by newbuntuxx on 2008-09-23
Hey...

I read a few pages here and there about Python. I am halfway through the: Dive Into Python book. I have a modest experince in Java and C. I also worked with Borland Delphi (long ago). So, I am not entirely a noob when it comes to programming.

My questions are:

1. Is it possible to compile python to native code and ship it in that format, so that the receiving end does not require an interperter to run the python code?

2. What is the best python gui toolkit to use, in terms of its ability to cross plat-form and its native look (and ease of use)?


thanks..

---

### Post by zolookas on 2008-09-23
If you want cross platform and native look, then Qt toolkit is probably the best choice. However, if you want to develop closed source applications, it will cost you money. If this is not acceptable for you, check wxwidgets. For example vlc player 0.8 was based on wxwidgets and 0.9 uses Qt.

---

### Post by SeanHodges on 2008-09-23
> **newbuntuxx said:**
> 1. Is it possible to compile python to native code and ship it in that format, so that the receiving end does not require an interperter to run the python code?

Native code for what? Windows? Linux? OSX?

The usual deployment in Linux is to create a package for your target Linux distribution(s). In the case of Ubuntu, you would create a .deb, which would be configured to depend on "python". This ensures that the user does not need to install Python automatically.

For Windows and OSX (which do not have package managers) you can use a packaging utility like py2exe or py2app to bundle the necessary dependencies into a self-contained executable, see:

[http://www.freehackers.org/Packaging_a_python_program](http://www.freehackers.org/Packaging_a_python_program)

> **newbuntuxx said:**
> 2. What is the best python gui toolkit to use, in terms of its ability to cross plat-form and its native look (and ease of use)?

I personally prefer PyGTK and Glade, its simple and fast to use. It's also in very common usage (as are wxWidgets and QT). This is a good tutorial site to get started:

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

The toolkits that zolookas mentioned are also well worth looking at.

---

### Post by hasanatkazmi on 2008-10-11
I think the best GUI library for python is Pythoncard. I have tried all GUI builders mentioned in this post but pythoncard is the easiest among all.

---

### Post by LaRoza on 2008-10-11
> **newbuntuxx said:**
> 
1. Is it possible to compile python to native code and ship it in that format, so that the receiving end does not require an interperter to run the python code?

[http://ubuntuforums.org/showthread.php?t=927962](http://ubuntuforums.org/showthread.php?t=927962)

> 
2. What is the best python gui toolkit to use, in terms of its ability to cross plat-form and its native look (and ease of use)?


[http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507)

---

### Post by The Cog on 2008-10-11
pythoncard sounds interesting. So I just installed it, but I can't find an entry point. The intro in the docs just says how to start it on windows and doesn't help. How on earth do you start it???

---

### Post by hasanatkazmi on 2008-11-04
> **The Cog said:**
> pythoncard sounds interesting. So I just installed it, but I can't find an entry point. The intro in the docs just says how to start it on windows and doesn't help. How on earth do you start it???

I was on NT when I used it, havn't tried it on Linux, but its a fact that their site speaks less about Linux

---

### Post by hasanatkazmi on 2008-11-04
well here is it:

try this

cd /usr/lib/python2.5/site-packages/PythonCard/samples/minimal
./minimal.py

you may use documentation for windows (because python behaves equally in both OSes), because for getting started, the only different thing was path :)

---

### Post by OutOfReach on 2008-11-04
> **newbuntuxx said:**
> 
1. Is it possible to compile python to native code and ship it in that format, so that the receiving end does not require an interperter to run the python code?
I don't have a lot of experience with this, but when I tried py2exe, the speed and general performance suffered.

> 
2. What is the best python gui toolkit to use, in terms of its ability to cross plat-form and its native look (and ease of use)?


thanks..
Let me be unbiased for a second. I'll give you the major toolkits.
GTK - Popular, has a native look *on GTK+ based enviroments* on Windows and KDE (don't know about Mac) it looks out of place. Written in C so performance wise it is good. A little harder to understand/code (from my experience).
Qt - Gaining popularity. Generally does have a native look. (QGtkStyle provides native look for GTK enviroments). Can be themed. Not just a GUI toolkit, it also provides libraries for Networking, XML parsing, Databases, Internationalization. You can also code custom widgets.

Hmm, now that I look at it, I am still leaning towards Qt. Oh well... :)

---

