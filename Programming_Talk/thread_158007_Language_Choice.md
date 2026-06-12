---
title: "Language Choice"
date: 2006-04-10
forum: Programming Talk
---

### Post by jethro10 on 2006-04-10
I'm sure its been asked a zillion times. It looks like it has, but I want help on a language choice for linux.
I am an asp.net VB developer on windows and have done stuff on Palms and Pocket PC's before.
I dont want the steep curve of C / C++ but dont want to hit a dead end soon.
want Visualy based tools ALA visual studio for forms design.

Preferably a cross platform tool as this is definatly my last language (I really do hope)

I was thinking python ? or Gambas Basic?
Now I lean to python because as I see it, it's more developed and the guys writing GUI Developers Tools are using the core python for compiling which has its own development team? reducing the load on the Front end designer. Whereas I see Gambas or similar as a GUI AND a language so it waters down the development on it?

Something for example that would be good enogh to write a product that installs a system tray icon (is that what its called in inux?) or to write a front end for a command line tool like ffmpeg or unrar etc.

In truth I dont really know.
Any ideas anyone.

Ta
Jeff

---

### Post by jethro10 on 2006-04-10
Doing some more reasearch, it looks like Glade is a GUI front end for lots of languages, so that seems a good choice I feel.

So is it Glade and Python?

Or what is this wxWidgets.

---

### Post by red_Marvin on 2006-04-11
I am a [FreeBASIC]("http://www.freebasic.net") user myself, and it should be quite easy to adapt to if you know vb.
It's like MSFT Qbasic but 32 bit and more powerful.
If you want a visual forms designer there is glade (but I prefer hard-coding the GUI),
but there also some basic compiler that is like VB for linux.

---

### Post by moephan on 2006-04-12
If you are a VB developer, I would suggest pairing Python (the language and class library) with pyGtk (the windowing toolkit). Here's some links:

Dive into Python to get you rolling:
[http://diveintopython.org/](http://diveintopython.org/)

Python tutorial:
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

The Python language reference:
[http://docs.python.org/ref/ref.html](http://docs.python.org/ref/ref.html)

The Python class library:
[http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

the pyGtk tutorial:
[http://www.moeraki.com/pygtkreference/pygtk2tutorial/](http://www.moeraki.com/pygtkreference/pygtk2tutorial/)

You might also want to link to the Gtk class library documentation. Unfortunately, it is all written in C, so a lot of the code is different then what you will write using the Python bindings:
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)

Coming from VB, I expect you will find Python and Gtk to be a very fun platform for writing your apps. You can start by just hand coding your Gtk code, and then start using Glade when your apps reach that level of complexity.

Cheers, Rick

---

### Post by Jessehk on 2006-04-13
I happen to love the Ruby language. It is not as popular as Python (yet), but it is growing rapidly. 

In my opinion, it has the power of Python (and more), in a much more OOP, elegant package. 

[http://www.ruby-lang.org](http://www.ruby-lang.org)

If you're interested, I'll post a few resources.

---

### Post by mostwanted on 2006-04-13
+1 for Ruby here. It's a really cool language and everyone who tries it comes to love it. True story.

---

### Post by pharcyde on 2006-04-14
Ruby is great.  I switched to Ruby from Perl and never looked back.

---

