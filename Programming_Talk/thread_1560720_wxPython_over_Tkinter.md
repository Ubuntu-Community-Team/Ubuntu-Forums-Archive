---
title: "wxPython over Tkinter"
date: 2010-08-25
forum: Programming Talk
---

### Post by CosmicFlux on 2010-08-25
Hey all!

I've recently started learning Python, specifically using the GUI Toolkits. I was learning Tkinter until I discovered wxPython. I noticed that when creating frames using wxPython, they have a more native feel than when done on Tkinter and, essentially, look more sleek. I guess my question is why would you, then, use Tkinter over wxPython in any situation?

Cosmic

---

### Post by dv3500ea on 2010-08-25
In my experience of GUI programming in perl, TK was probably the easiest GUI platform to program for but looks really ugly. Shoes is the easiest GUI I've come across (apart from DHTML, which needs a web browser) and looks good but it is only available for Ruby.

TK is good for small tasks due to its simplicity, though often zenity has replaced it in such tasks for me.

---

### Post by memilanuk on 2010-08-25
Somewhere along the line I've gotten the impression that there are more current versions of Tkinter than what Python ships with, ones that are closer to wxPython in appearance and function.  Which of course begs the question: why is Python still shipping with tkinter v.8.4, which seems to be driving people *away*?

---

### Post by Simian Man on 2010-08-25
TK is a horrible GUI toolkit that doesn't look good on any platform.  It doesn't matter which version of Tkinter you use, it will always look bad.

---

### Post by memilanuk on 2010-08-25
I dunno - this looks okay to me...

[http://tktable.sourceforge.net/tile/](http://tktable.sourceforge.net/tile/)

---

### Post by juancarlospaco on 2010-08-25
> **Simian Man said:**
> TK is a horrible GUI toolkit that doesn't look good on any platform.  It doesn't matter which version of Tkinter you use, it will always look bad.

**NO**

[IMG]http://file.status.net/identica/juancarlospaco-20100624T021321-qapycyp.jpeg[/IMG]

[IMG]http://img23.imageshack.us/img23/5405/tooltipscvfacil2.jpg[/IMG]   [IMG]http://img580.imageshack.us/img580/3816/iconocvfacil2.jpg[/IMG]

*FYI compare TK speed Versus Wx Speed.*
:D

---

### Post by Simian Man on 2010-08-25
Even with improved TK themes, it still doesn't look like a native application on any Linux desktop.  wx looks native on virtually every desktop in existence except KDE (and even then still closer than TK with one of the GTK-QT engines).  That doesn't always matter, but for apps you are going to distribute nativity is a very good thing.

Also there should be virtually no speed differences between wx and TK.  The UI toolkit is basically never the bottleneck in speed - especially when using a dynamic language anyway.

---

### Post by memilanuk on 2010-08-25
Is wxPython available for Python 3.1?  Last I heard if you wanted to use wxPython, you had to stay with Python 2.6 for the foreseeable future... vs. Tkinter which supports Python 3.1 *now*.  Why they ship it with 8.4 instead of 8.5 (and tile) I still don't under...?

---

### Post by juancarlospaco on 2010-08-25
Try it your self, wx is slower.

wx still stuck on 2.x series of python.

---

