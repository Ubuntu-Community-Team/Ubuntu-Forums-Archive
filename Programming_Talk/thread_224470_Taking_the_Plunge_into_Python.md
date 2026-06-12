---
title: "Taking the Plunge into Python"
date: 2006-07-28
forum: Programming Talk
---

### Post by agger on 2006-07-28
I'm working through Mark Pilgrims "Dive into Python" as supplied in the Ubuntu 6.06 distribution, and it seems to be a very quick way to learn a powerful language.

Up till now, the only "IDE" I've been using is vi(m) and the command line. It's getting a but too limited though, and I was wondering ...

Anyone got any idea which of the available IDEs for Python work best? I downloaded Eclipse, but am having trouble finding out how to get it rolling with Python (seems more geared to Java "out of the box").

As for that or any other IDE, my criteria would be that it should somewhat resemble MSVC6 and be easy to figure out - what little time I have I'd prefer to spend learning the language rather than learning the IDE.

---

### Post by jordilin on 2006-07-28
I've tried several IDEs, such as eric3, spe, boa constructor... The one I would choose for its ease of use is eric3. It's a kde/qt app.  I use it to learn, but I prefer using an editor like emacs, since I prefer coding python GTK apps.

---

### Post by incubus on 2006-07-28
Dear agger,

If you like eclipse, try pydev:
[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

It works pretty well, I suggest following the tutorial there.  You may need to use the latest version of eclipse (3.2), which is very easy (just download and run ./eclipse).

Other IDEs to try are WingIDE and SPE.  I myself always come back to the combination of IPython (great for introspection) and Vim (where you can also have syntax highlighting).

By the way, other good tutorials are a Byte of Python and the one by Guido himself.  There's also a wiki-based tutorial hosted on infogami.

Hope it helps!  Python is fun.
incubus

PS: Yet another one is Komodo by ActiveState.  It's not free, but I found a coupon browsing digg.

---

### Post by thumper on 2006-07-28
I have to agree with **jordilin**, I use emacs to edit all my python.  There is a good python mode for it.

I find IDE's overrated in most respects.

---

### Post by jordilin on 2006-07-28
> **thumper said:**
> I have to agree with **jordilin**, I use emacs to edit all my python.  There is a good python mode for it.

I find IDE's overrated in most respects.
Yes, emacs has one of the best python modes out there :D

---

### Post by agger on 2006-07-28
> **jordilin said:**
> Yes, emacs has one of the best python modes out there :D
Is it easy to use - the python-mode for emacs, I mean?

And how do you get started - open a Python file and choose "help"?

---

### Post by jordilin on 2006-07-28
> **agger said:**
> Is it easy to use - the python-mode for emacs, I mean?

And how do you get started - open a Python file and choose "help"?

First of all, you must install the package python-mode. Then, if you open a python file name.py by issuing:
```
emacs name.py
```
you'll have syntax highlighting and indentation.

---

### Post by Note360 on 2006-07-28
Vi(m) limited?? Where are you from? I would suggest Scribes or Gedit for a simple effecient GUI editor.

---

### Post by agger on 2006-07-28
When I say that vi(m) is limited it's mainly because I normally work in a Unix environment so I only use the vi features, and in that sense vi *is* my simple, lightweight editor of choice.

I already tried Eclipse + pydev, by the way, and it actually looks cool and easy to use, but it's *very* sluggish on my old PC - I guess it's mean old Java hogging the ressources. 

So I got the python-mode for emacs and will try this and probably the Boa Constructor out as well. Thanks for all the tips, at all rates :-)

---

### Post by Note360 on 2006-07-28
Oh I forgot the Cream extension for Vi I havent got it working though but may be useful for you

---

### Post by Daverz on 2006-07-29
Here's another vote for emacs, specifically XEmacs.  pydev has a lot of compelling features, but I don't like the way it forces you to use to create a project and a package just to write some code.

I suggest using the xfonts-jmk package to get a usable font (neep-alt).

I've tried eric3, but the way it throws a gazillion toolbar icons at you seems to show a lack of taste IMO.

---

### Post by agger on 2006-07-29
A very simple thing I've discovered is IDLE, which seems to be some sort of "official" Python IDL (hosted at python.org).

It's really just an interactive shell with files opening in GEdit-style editor windows, but with debugger integration and some very basic path and class browsers. I think I'll give it a shot and if I'm not satisfied, I'll turn to Emacs. And now, back to Dive Into Python ...

---

### Post by forrestcupp on 2006-07-29
SPE is my favorite.  Dr Python is good, but too simple.  Eric has too much stuff on the screen.  SPE was just right for me.

---

### Post by Thirsteh on 2006-07-29
The definite best Python (and other high-level languages) IDE I've used in both Windows and Linux is Komodo from ActiveState. It's a commercial application, but it knocks the socks off Eclipse with PyExtentions.

---

