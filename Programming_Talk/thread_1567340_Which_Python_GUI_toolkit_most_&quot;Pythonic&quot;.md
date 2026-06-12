---
title: "Which Python GUI toolkit most &quot;Pythonic&quot;?"
date: 2010-09-03
forum: Programming Talk
---

### Post by xaegis on 2010-09-03
Hello all, I've been looking at Glade, QT4 and Wx for a while now and I was just wondering which one of these (or any at all) is the most "Pythonic?"
By Pythonic; I mean whose syntax, structure, and usage is most similar to proper python cannon and ideology.

I am aware of tk but I would like a bit more flexibility (signal/slots, and GUI code not embedded in/cluttering my software code) and the ability to use a GUI designer so that I'm not making all my widgets up from scratch each time, and that my window designs are reusable and easily portable.

I really like glade and especially the quickly development suite but I need a more comprehensive tutorial and cant seem to find one on the Internet anywhere(that is not completely out-dated). 

So what does everyone think?

:)

---

### Post by diesch on 2010-09-03
If you can read German (or what some translation tool makes out of it)  [http://www.florian-diesch.de/doc/python-und-glade/](http://www.florian-diesch.de/doc/python-und-glade/) may be some help.

---

### Post by xaegis on 2010-09-03
> **diesch said:**
> If you can read German (or what some translation tool makes out of it)  [http://www.florian-diesch.de/doc/python-und-glade/](http://www.florian-diesch.de/doc/python-und-glade/) may be some help.
My German is pretty bad. I'm not sure it would be very time effective for me to learn German in order to learn GLADE. :)

---

### Post by juancarlospaco on 2010-09-03
**Tk**
Is built-in on Python, the first on support 3.x, actively maintained for Python.

Random example, my splash screen:
[IMG]http://file.status.net/identica/juancarlospaco-20100624T021321-qapycyp.jpeg[/IMG]

WYSIWYG GUI-Builder for Python-TK:
[http://sourceforge.net/projects/spectcl/files/GUI%20Builder/](http://sourceforge.net/projects/spectcl/files/GUI%20Builder/)

TK FULL Manual:
[http://infohost.nmt.edu/tcc/help/pubs/tkinter.pdf](http://infohost.nmt.edu/tcc/help/pubs/tkinter.pdf)

:)

---

### Post by nvteighen on 2010-09-04
I'm not sure... Tk (Tkinter?) comes from Tcl/Tk, GTK+ comes from C, Qt comes from C++... And I've always felt that PyGtk and PyQt, although they do a great job in making the library work in the most Pythonic way, they still "feel" like C and C++, respectively...

I'm not sure about why I have this feeling. It may be because it seems unwise to extensively modify the API to something that doesn't resemble the original API... I don't know, maybe the thought behind this is that people learning PyGtk should be able to migrate easily to the GTK+ C library (or in the Qt case, C++) and viceversa.

I've never used Tk, just seen some code and it didn't look Pythonic at all...

This post is crap, I guess... just based on partial impressions... :P

---

### Post by xaegis on 2010-09-04
This post is all about feeling. I've been learning GLADE and QT this week and I just had the "feeling" that GUI creation using these tools felt somehow different than when I was programming for the terminal in python. I'm stuck with QT now because they have the best reference I can find: The Book :Rapid GUI Programming with Python and QT. But it feels somewhat alien. I was just looking for other peoples opinions on the matter or if my suspicions were unfounded and un-corroborated.

---

