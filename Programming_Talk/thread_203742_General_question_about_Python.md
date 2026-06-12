---
title: "General question about Python"
date: 2006-06-25
forum: Programming Talk
---

### Post by DirtyJay on 2006-06-25
I have decided to explore Python as a programming language.  My first thoughts on looking around, I get the feeling that Python is a language that only works in the Python shell?  What I mean to ask is, is it a lauguage meant only to be effectively run from the terminal?  ...can you program with it to work in Gnome?  .. create windows, buttons, menu's etc.?  From what I can tell, even working in the Python shell, it appears that it is very limited in the way it can output to the screen.    ..to place text anywhere on the screen, draw simple shapes and lines.

Is this a reasonable conclusion of Python or do I need to dig a little bit deeper.

Thanks

---

### Post by LordHunter317 on 2006-06-25
[QUOTE=DirtyJay]My first thoughts on looking around, I get the feeling that Python is a language that only works in the Python shell?[/quote]No, not in the least.

> What I mean to ask is, is it a lauguage meant only to be effectively run from the terminal?  ...can you program with it to work in Gnome?  .. create windows, buttons, menu's etc.?Yes, with the right libraries.  Look at pygtk.

> From what I can tell, even working in the Python shell, it appears that it is very limited in the way it can output to the screen.    ..to place text anywhere on the screen, draw simple shapes and lines.Python's core libraries are, but there is ncurses support.

But the same is true of shell, C, C++, perl, virtually any UNIX language.

---

### Post by DirtyJay on 2006-06-25
Thank you for the pointer.

I will do some more digg'n!

---

### Post by digby on 2006-06-25
Just for an example to look at, the interface for cedega is written in python, I believe.

---

### Post by DirtyJay on 2006-06-26
ok, so I have done a bit of digging.  Does python already have ncurses installed?  Do I need to do some downloading?  Where do I put these files? :confused: 

Sorry guys, I'm a bit clumsy at the mechanics of this.

---

### Post by Daverz on 2006-06-26
[QUOTE=DirtyJay]ok, so I have done a bit of digging.  Does python already have ncurses installed?[/QUOTE]

Yes, curses is a standard module.  You might also want to try snack, which is an interface to the slang screen handling library.

[http://www.wanware.com/tsgdocs/snack.html](http://www.wanware.com/tsgdocs/snack.html)

> Do I need to do some downloading?

The first thing I'd do is install the python docs (package name python-doc) and look the library documentation over to see what is already included.  You might also want to install the devhelp package to read the docs with.

> Where do I put these files?

Usually, python modules have a setup.py script, so you can install a module by running this script with "install" as an argument:

sudo python setup.py install

The Ubuntu repositories have tons of python modules, so may not need to do even this.

---

