---
title: "Please recommend some Python GUI tools and tutorials"
date: 2006-03-13
forum: Programming Talk
---

### Post by s|k on 2006-03-13
I'm wanting to learn how to program in GUI on Linux with Python, any recommendations? Thanks. :)

---

### Post by puddpunk on 2006-03-13
I never really found a great one - I still prefer gedit/vim and a console.

There are python plugins for most popular Intergrated Development Environments like MonoDevelop, Eclipse, KDevelop etc... but they all seemed to add a layer of abstraction over python that wasn't really needed.

Honestly, if you want to learn the absolute best way is to load up some of the tutorials on python.org open a console and play around with the interpreter and a simple text editor. When you learn using the IDE you're severly limiting yourself about ways to look at the language.

If you really want to have a smash at it with an IDE, try Eric3. It has quite a few dependancies though (like Qt etc...).

---

### Post by Barrakketh on 2006-03-13
[QUOTE=puddpunk]There are python plugins for most popular Intergrated Development Environments like MonoDevelop, Eclipse, KDevelop etc... but they all seemed to add a layer of abstraction over python that wasn't really needed.[/quote]
To hell with that.  I happen to like having code completion (and more importantly, access to a function's docstrings) when picking up a language.  I also strongly dislike console debuggers.

Personally, I use PyDev for Eclipse.

[quote=s|k]I'm wanting to learn how to program in GUI on Linux with Python[/quote]
What do you mean by "program in GUI"?  If you're wanting to use a GUI toolkit, take a look at [PyGTK](http://www.pygtk.org).  You may wish to learn Python first before you jump on learning GTK+ though.

---

### Post by puddpunk on 2006-03-13
> To hell with that. I happen to like having code completion (and more importantly, access to a function's docstrings) when picking up a language. I also strongly dislike console debuggers.

Each to their own - I've always viewed code completion as a crutch while learning a language. When you've become proficient it's a convenience thing. Also, I've never had to use a debugger for python (thank god!) console or otherwise. I feel that if you can't write software in a language using an editor and compiler/interpreter you don't really know the language.

Python provides access to it's function documentation inside the interpreter - try: print open.__doc__.

The point is that the beauty of python is it's simplicity, why gunk it up with things that make it more complicated? When I first had to develop Java for a job I used vim. Java is a lot more complicated than python (many files, classes, objects) and I found it was a lot better to work with a GUI to manage that. Now all my Java work is done in eclipse and I find it a lot better.

Don't get me wrong, though. I'm not one of those archaic console geeks that insist everything should be done in vim and use the terminal all the time :) GUI's and IDE's have their place but that place isn't when you're starting out.

---

### Post by krypto_wizard on 2006-03-13
SPE is also very good

---

### Post by gord on 2006-03-14
ActiveState Komodo is great :) you have to shell out some money but its worth it :)

---

### Post by MicahCarrick on 2006-03-16
If you want to program Gnome GUI applications using GTK+ and Python, you may want to check out this tutorial: [Developing with Gnome In C, C++, Perl, and Python]("http://www.gnome.org/~newren/tutorials/developing-with-gnome/")

Though I work in C so I can't judge how good it is for Python.  In any case, good luck.

---

### Post by engla on 2006-03-16
My setup is very strange, but hasn't matured yet...

So far it looks like this:
[LIST]
[*]The text editor [Scribes]("http://scribes.sourceforge.net/"), a great but "easy" texteditor that helps me via syntanx colors and **text snippets**
[*]A **screen** session setup with split screen; a shell with the project directory (for running/building the project) and a python console in the other pane.
[*]**Glade** for UI building -- works fine with the python bindings. Depending on context one might choose to build some parts of the interface in just code, though.
[*]**Autotools** for building/packaging, probably not the best choice for a fast/simple/intuitive solution, but I think it's the best for endusers when they are to install the package.
[/LIST]

Yeah, and I use [PyGTK]("http://pygtk.org/") to build my ui with python. They have a [general tutorial collection]("http://pygtk.org/tutorial.html").

---

### Post by anti-net on 2006-03-16
I just started learning python, im using Glade and PyGTK to make my apps, seems to be good, and theres lots of community support :)

---

