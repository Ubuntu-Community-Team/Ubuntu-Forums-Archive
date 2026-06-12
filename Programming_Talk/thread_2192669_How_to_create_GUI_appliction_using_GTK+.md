---
title: "How to create GUI appliction using GTK+"
date: 2013-12-09
forum: Programming Talk
---

### Post by Whale Forever on 2013-12-09
I want to create a GUI application using GTK, i have basic programming skill for python. so what i want to ask:


[LIST=1]
[*]is there a tutorial guide to create an ubuntu application using python and GTK ? 
[*]any book to guide me ? 
[*]is there a template or convention to outline the program ? 
[/LIST]


thanx for your answer :)

---

### Post by oldfred on 2013-12-09
Moving you from tutorials to programing. Tutorials is for posts that are tutorials.

 pygtk3 gtk.AboutDialog(), help
[http://ubuntuforums.org/showthread.php?t=2092094](http://ubuntuforums.org/showthread.php?t=2092094)

I started with gtk2, but now am trying pyqt, so not sure what all the updates are. Most of these then are older.
I used glade to create gui.
[http://www.gtkforums.com/](http://www.gtkforums.com/)
[http://www.zetcode.com/gui/pygtk/](http://www.zetcode.com/gui/pygtk/)
[http://blog.borovsak.si/2009/09/glade3-tutorial-1-introduction.html](http://blog.borovsak.si/2009/09/glade3-tutorial-1-introduction.html)
[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

---

### Post by Anonimista on 2013-12-09
(Also a novice) 
I fount this tutorial useful:

[The Python GTK+ 3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/")

It seems that PyGObject is the way to go (instead of PyGtk which is obsolete) which would make many online examples and tutorials obsolete ([PyGObject for Beginners - Fedora People]("http://www.google.ba/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CCQQFjAA&url=http%3A%2F%2Fpfrields.fedorapeople.org%2Fpresentations%2FOhioLF2011%2FPyGObject.pdf&ei=m_ClUpjCIee7ygP_44DIDw&usg=AFQjCNGESuynOabZqYV8Wizd-bG7TffFLQ&sig2=m2JZsgZREHOCz0bTYZ3QGg") PDF presentation - very informative). I figured out that PyGtk examples (the old ones) begin with:

```
import gtk
```

while the PyGObject (the new ones) have:

```
from gi.repository import Gtk
```

I also installed a tool called [Quickly]("https://wiki.ubuntu.com/Quickly") which creates PyGObject application templates. Quickly is a command line tool and the workflow is like this: Use it to start Glade and design a UI, then open the created files in GEdit to write the code.

I am still confused though, it seems that the main GUI toolkit for Ubuntu won't be Gtk but Qt (mentioned in this thread: [What about forking the good Gnome applications for Unity?]("http://ubuntuforums.org/showthread.php?t=2191936")) There is a thing called [Ubuntu SDK]("http://developer.ubuntu.com/apps/") which installes QT Creator with Ubuntu application templates. I installed it but Python support doesn't seem to complete yet. The latest version is Qt 5 but I wasn't able to find Python 2.7 bindings for it on 12.04 LTS. I downloaded the source and compiled it (it was a rather painless process). The workflow as I understand it is like this: Create a form in QT Creator design view, save it and translate the saved file to a python class using a command line tool called pyuic5. Then use the created class in Python (It is possible to create a Python source file with Qt Creator).

So I managed to create the 'Hello, World' scripts both in but am uncertain which way to go (PyGObject or PyQt5). To add to the confusion there appears to a problem with PyQt license if you want to create commercial applications with it and there is another Qt binding for Python called PySide. :confused:

---

### Post by Whale Forever on 2013-12-15
> **Anonimista said:**
> (Also a novice) 
I fount this tutorial useful:

[The Python GTK+ 3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/")

It seems that PyGObject is the way to go (instead of PyGtk which is obsolete) which would make many online examples and tutorials obsolete ([PyGObject for Beginners - Fedora People]("http://www.google.ba/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CCQQFjAA&url=http%3A%2F%2Fpfrields.fedorapeople.org%2Fpresentations%2FOhioLF2011%2FPyGObject.pdf&ei=m_ClUpjCIee7ygP_44DIDw&usg=AFQjCNGESuynOabZqYV8Wizd-bG7TffFLQ&sig2=m2JZsgZREHOCz0bTYZ3QGg") PDF presentation - very informative). I figured out that PyGtk examples (the old ones) begin with:

```
import gtk
```

while the PyGObject (the new ones) have:

```
from gi.repository import Gtk
```

I also installed a tool called [Quickly]("https://wiki.ubuntu.com/Quickly") which creates PyGObject application templates. Quickly is a command line tool and the workflow is like this: Use it to start Glade and design a UI, then open the created files in GEdit to write the code.

I am still confused though, it seems that the main GUI toolkit for Ubuntu won't be Gtk but Qt (mentioned in this thread: [What about forking the good Gnome applications for Unity?]("http://ubuntuforums.org/showthread.php?t=2191936")) There is a thing called [Ubuntu SDK]("http://developer.ubuntu.com/apps/") which installes QT Creator with Ubuntu application templates. I installed it but Python support doesn't seem to complete yet. The latest version is Qt 5 but I wasn't able to find Python 2.7 bindings for it on 12.04 LTS. I downloaded the source and compiled it (it was a rather painless process). The workflow as I understand it is like this: Create a form in QT Creator design view, save it and translate the saved file to a python class using a command line tool called pyuic5. Then use the created class in Python (It is possible to create a Python source file with Qt Creator).

So I managed to create the 'Hello, World' scripts both in but am uncertain which way to go (PyGObject or PyQt5). To add to the confusion there appears to a problem with PyQt license if you want to create commercial applications with it and there is another Qt binding for Python called PySide. :confused:

isn't PyQt Free ?

---

### Post by Anonimista on 2013-12-19
Yes, but apparently [it's not that simple]("http://askubuntu.com/questions/339723/can-i-sell-my-pyqt4-app-without-having-a-pyqt-license"). I won't be using PyQt for anything commercial,  so I didn't do any research beyond that thread, but it may be a thing to consider depending on what you intend.

---

