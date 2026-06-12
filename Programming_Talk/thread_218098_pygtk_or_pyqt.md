---
title: "pygtk or pyqt?"
date: 2006-07-18
forum: Programming Talk
---

### Post by jordilin on 2006-07-18
I have been learning python and I would like to do some gui programming, and now (as always in Linux ;-)) I'm facing this question: Which is best pygtk or pyqt?

---

### Post by Daverz on 2006-07-18
Pygtk has better documentation (of the *python* api; I'm sure qt has excellent C++-based docs).  I still really don't know much about qt.

So some comments on pygtk:

* Has a very extensive set of widgets, even if they aren't always easy to use (I'm thinking here of the List/Tree infrastructure.  But see kiwi below, which has a simplified list widget).

* Fairly fast and efficient.

* Somewhat low-level in the sense that it's just a toolkit.  There's no data-binding API, for example.  But check out kiwi, which makes this easy.

* I like the Gtk aesthetics.  The default look of qt demo apps on ubuntu is somewhat tk-like.  Yuck.  I suppose they might look better on kubuntu.

* Glade, the gui builder, has fallen way behind.  A python replacement, Gazpacho, has a way to go yet.  I don't think it's that hard to do layout "by hand" in Python,  though.

* Works well on win32 and is easy to install there.  I'm having problems getting pyqt working on windows.

Everything pygtk: [http://pygtk.org/](http://pygtk.org/)

---

### Post by forrestcupp on 2006-07-25
I like pygtk.  I don't know anything about qt, but I know pygtk can be used on Windows, too, which means crossplatform stuff will be easy.  After only a few days of learning pygtk in my spare time, I have already created a game for my 2 year old boy.  It's easy to use, and it looks nice.

---

### Post by asimon on 2006-07-26
> **Daverz said:**
> Pygtk has better documentation (of the *python* api; I'm sure qt has excellent C++-based docs).  I still really don't know much about qt.
For PyQt v4 there is now a complete [Class Reference](http://www.riverbankcomputing.com/Docs/PyQt4/html/classes.html) which has been adapted from the excellent Qt documentation.

> **Daverz said:**
> 
* Has a very extensive set of widgets, even if they aren't always easy to use (I'm thinking here of the List/Tree infrastructure.  But see kiwi below, which has a simplified list widget).
Well, Qt has also a very extensive set of widgets.  ;-)

> **Daverz said:**
> 
* Fairly fast and efficient.
The general opinion is that Qt is faster then GTK+. But I think they are usually both fast enough.

> **Daverz said:**
> 
* Somewhat low-level in the sense that it's just a toolkit.  There's no data-binding API, for example.  But check out kiwi, which makes this easy.
Yes Qt also has abstractions of network sockets, threads, Unicode, regular expressions, SQL databases, SVG, OpenGL, XML, but is this really an advantage to GTK+ that doesn't have these things? Usually GTK+ apps don't end smaller in their resource footprint then Qt ones.

> **Daverz said:**
> 
* I like the Gtk aesthetics.  The default look of qt demo apps on ubuntu is somewhat tk-like.  Yuck.  I suppose they might look better on kubuntu.
Yes Qt3's default look was terrible. The Qt4 default look is much better.

> **Daverz said:**
> 
* Glade, the gui builder, has fallen way behind.  A python replacement, Gazpacho, has a way to go yet.  I don't think it's that hard to do layout "by hand" in Python,  though.
PyQt4 includes pyuic so that Qt's designer can be used for RAD development. I prefer designer to glade but as glade Qt's designer has it's shortcummings. Depending on the complexity or level of detail you want to control there is not way to escape programming the GUI by hand.

> **Daverz said:**
> 
* Works well on win32 and is easy to install there.  I'm having problems getting pyqt working on windows.
At least for PyQt4 there is a binary installer for Windows. I never tried it but it should work by just clicking a couple of times with your mouse.

> **Daverz said:**
> 
Everything pygtk: [http://pygtk.org/](http://pygtk.org/)
For PyQt: [PyQt](http://www.riverbankcomputing.co.uk/pyqt/)

;-)

---

### Post by mostwanted on 2006-07-26
> **forrestcupp said:**
> I like pygtk.  I don't know anything about qt, but I know pygtk can be used on Windows, too, which means crossplatform stuff will be easy.  After only a few days of learning pygtk in my spare time, I have already created a game for my 2 year old boy.  It's easy to use, and it looks nice.

Gtk+ was originally designed as a cross-platform toolkit for The GIMP so PyGTK apps run in Windows as well.

---

### Post by iamah on 2006-07-26
[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)
I don't know much but I never liked Qt(KDE traumas) very much, and this article convinced me to Gtk.

---

### Post by Daverz on 2006-07-26
> **asimon said:**
> For PyQt v4 there is now a complete [Class Reference](http://www.riverbankcomputing.com/Docs/PyQt4/html/classes.html) which has been adapted from the excellent Qt documentation.


That's good to know, thanks.  I may end up using it because a friend wants to use it on a project.  However, I'd like to get it running on windows (and working with py2exe), so that we have a larger user base.

> 
The general opinion is that Qt is faster then GTK+. But I think they are usually both fast enough.


The "general opinion"?  Is that like "Some people say..."?

> 
Yes Qt also has abstractions of network sockets, threads, Unicode, regular expressions, SQL databases, SVG, OpenGL, XML, 


I'm aware of some of these, but I'd prefer use python's abstractions over Qt's.  To me these seem to be dubious things to add to a GUI framework, but I understand that it makes life easier for C++ programmers.

> 
but is this really an advantage to GTK+ that doesn't have these things? 


I was being descriptive, not claiming any advantages.

> 
Yes Qt3's default look was terrible. The Qt4 default look is much better.


I was talking about the pyqt4 demos.  These still look very Tk-ish to me.  Is there a way to improve the looks?

> 
At least for PyQt4 there is a binary installer for Windows. I never tried it but it should work by just clicking a couple of times with your mouse.


I should have been more explicit about the problem I was having.  I've installed both the Qt4 evaluation package (the demos work) and PyQt4 for windows.  I get a library error when I try to run any PyQt4 demos, something about a procedure entry point not being found.  I haven't had the time to follow up on the error.

---

### Post by iamah on 2006-07-26
Could someone help me? Here's my noob problem:
[http://www.ubuntuforums.org/showthread.php?t=223460](http://www.ubuntuforums.org/showthread.php?t=223460)

---

### Post by Daverz on 2006-07-26
> **iamah said:**
> Could someone help me? Here's my noob problem:
[http://www.ubuntuforums.org/showthread.php?t=223460](http://www.ubuntuforums.org/showthread.php?t=223460)

I'm sure everyone saw it, there's no need to post in other threads.

A syntax error has nothing to do with pygtk.  Try running /usr/lib/python2.4/tabnanny.py on your source.

---

### Post by Daverz on 2006-07-26
> **Daverz said:**
> I should have been more explicit about the problem I was having.  I've installed both the Qt4 evaluation package (the demos work) and PyQt4 for windows.  I get a library error when I try to run any PyQt4 demos, something about a procedure entry point not being found.  I haven't had the time to follow up on the error.

OK, apparently I installed the wrong package.  Once I installed the GPL edition (which will also install MINGW for you), it worked:

[http://www.trolltech.com/developer/downloads/qt/windows](http://www.trolltech.com/developer/downloads/qt/windows)

So now all I need is a good tutorial for pygtk4.

---

### Post by iamah on 2006-07-26
> **Daverz said:**
> I'm sure everyone saw it, there's no need to post in other threads.

A syntax error has nothing to do with pygtk.  Try running /usr/lib/python2.4/tabnanny.py on your source.

well, I don't see your tip on the other thread... thanks, it was an identation problem indeed

---

### Post by kripkenstein on 2006-07-27
Other than pygtk and pyqt, you might consider [wxPython]("http://www.wxpython.org/"). It's cross-platform, so code can run on Linux (via gtk), Mac, or Windows.

---

### Post by asimon on 2006-07-27
> **Daverz said:**
> So now all I need is a good tutorial for pygtk4.
Do you mean pyqt4? ;-)
There are some tutorials listed in the [Wiki](http://www.diotavelli.net/PyQtWiki/DevelopmentWithPyQt) but I fear none of them is especially for version 4.

---

### Post by TGArcher on 2007-05-04
See, I don't mind using gtk apps, but programing is another story. I'm personally learning python myself and I have a friend who has learned both. His comment is that with GTK, you find youreslf scratching your head wondering why they do some things, or just wondering why. With Qt, the modules speek for themselves and are very easy to use. QtPaint, QtWidget, etc. are some of the names of the module names. I would recommend PyQt at first, see how you like it, then do some research into GTK. Heck, you may like both, but look into Qt first cause it has powerful modules that are easy to use and easy to remember when you get going. Oh, and it's cross platform and is used by alot of people you may have heard of ( Google, Skype, KDE, Lockheed Martin ...).

---

