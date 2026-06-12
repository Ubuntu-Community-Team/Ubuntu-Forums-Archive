---
title: "Best Programing Languages for GENERAL Linux?"
date: 2007-04-30
forum: Programming Talk
---

### Post by chris062689 on 2007-04-30
I want to begin developing programs for Linux.
I want them to be compatable with GNOME and KDE without any  extra software downloading.
I want to be able to interact with databases.
I want to be able to make GUIs (could there even be something like Visual Basic's window maker?!)

---

### Post by LaRoza on 2007-04-30
Python is easy to learn, powerful, and connects to databases easily.

It will work in Linux and Windows too.

---

### Post by RichyJohnnyer on 2007-04-30
> **LaRoza said:**
> Python is easy to learn, powerful, and connects to databases easily.

It will work in Linux and Windows too.

NO U. Staop saying THINGS that are nut true!

---

### Post by walesmd on 2007-04-30
I'm a fan of both Python and Ruby - both of which are cross-platform.

I dabbled in some LUA when working on World of Warcraft interface mods - it's a strong contender as well, which is also cross-platform.

---

### Post by zetsumei on 2007-04-30
I prefer C++ and Python besides web programming languages...

---

### Post by misconfiguration on 2007-04-30
I vote PERL.

---

### Post by Wybiral on 2007-04-30
There's a sticky with all kinds of language info... Don't waste your time with questions like this. Do some research, that's what programming is all about (you need to be able to learn for yourself).

Never-the-less, I recommend:
   Python for high level scripting
   C for low level byte crunching
   Javascript+PHP for web development

All of them can interface with a database, and C and Python can both be used to create GUI's.

---

### Post by AdamG on 2007-04-30
Another +1 for Python. The wxPython library makes cross-platform GUIing doable without pulling your hair out, and despite being an interpreted language, I've never run into any situation (except maybe pure number-crunching) where Python wasn't "fast enough." 

My experience with Python and databases has likewise been good. MySQLdb and psycopg2 both work well for MySQL and PosgreSQL, respectively. There is also SQLite in the stdlib which means you can prototype database-driven apps without even installing an RDBMS daemon!

By and large, both GNOME and KDE can run each other's applications. However (and maybe this is just my illusion - can someone correct me?) I tend to find that running GTK apps in KDE is less of a problem than running QT apps in GNOME. Since wxWidgets, and thus wxPython, uses GTK anyway, the moral of this paragraph is "use wxPython".

---

### Post by Toxe on 2007-04-30
C and one year later C++.

---

### Post by samjh on 2007-05-01
> **chris062689 said:**
> I want them to be compatable with GNOME and KDE without any  extra software downloading.

If that is one of your requirements, I'm afraid you are limited to making console-based programs compiled into executable binaries.  C/C++ are probably the best.

Any GUI interface programmed in any language other than C or C++ will likely need extra software to be downloaded.  The extent of the extra software will depend on the version of Linux.  Python programs with Gnome-based GUI will need PyGTK, for example.

That requirement also excludes most interpreted languages, including Python, depending on the target Linux distribution.

In summary: that requirement just isn't practical. ;)

Assuming you are going to drop that one, then I'd recommend any of:
Ada
C
C++
C#
FreeBasic
GAMBAS
Java
Pascal
Python
VB
... and more, depending on your existing expertise with programming.

---

### Post by Paul Miller on 2007-05-01
Let me clarify something a bit.  You *can* create GUI apps in Python that are portable to Windows, OSX, KDE, GNOME, and many other systems using only libraries in the python distribution.  However, Python's default GUI toolkit, TKinter, doesn't look "native" on any platform, really.  Your code will work, but (particularly on OSX) your app will look noticeably "different."  

This may or may not be a problem for you.  (In truth, I don't think TKinter apps look *that* odd or out of place, but YMMV.)  If it is, then, if you choose Python as your programming language, you'll need to use some libraries such as wxPython, PyQt, PyGTK, or GNOME-Python to implement your GUI.

I love Python, myself.  I always have the latest version installed, because using it makes programming *fun*.  I find it's highly expressive and allows me to code my algorithms so they look like their mathematical definition.  This makes it easier to tell whether the code is correct or not.  

It's not perfect, of course.  Where Python may disappoint you is in the are of performance.  There are ways of getting around this; at this point, I'd recommend using pyrex or ctypes, since the C API is undergoing heavy change come Python 3.0.

---

### Post by chris062689 on 2007-05-01
So what kind of GUI libary should I use to provide "realistic" GUI for all of the operating systems?
TKinter looks fine to me, I realize it's not Luna theme, but meh...

Are they going to plan on improving speed issues soon? :/

(I'm pretty much sold on python)

---

### Post by chris062689 on 2007-05-01
What's the best IDE for Linux? Kdevelop I assume...
What about Windows? (I'm at school right now, and want to start!)

---

### Post by Tomosaur on 2007-05-01
> **chris062689 said:**
> What's the best IDE for Linux? Kdevelop I assume...
What about Windows? (I'm at school right now, and want to start!)

A great generic IDE is Eclipse. It defaults to Java, but it has plugins for many other languages. It's very intuitive, but I find the Pydev plugin to be a little slow and incomplete. I tend not to use IDEs much, but when I do, I use Eclipse.

You can just use a text editor and keep the web-reference for python open in your browser, though, it's pretty much the most efficient way to do it.

---

