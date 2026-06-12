---
title: "How to learn Python fast ?"
date: 2006-01-25
forum: Programming Talk
---

### Post by krypto_wizard on 2006-01-25
Hi,

I recently started learning Python after getting recommended from so many coding gurus. I was programming in C before. I want to implement a Project in python pretty soon.

What is the best learning method for python. Should I read books and get familiar first or get started after some initial lessons and open books and tutorials as and when needed. Guys, I really need your guidance in that.

Can you guys share your experience how you mastered python ?

Thanks

---

### Post by nszabolcs on 2006-01-25
[QUOTE=krypto_wizard]Hi,
What is the best learning method for python. Should I read books and get familiar first or get started after some initial lessons and open books and tutorials as and when needed. 
[/QUOTE]

my recipie: 
[LIST]
[*] Run through the official tutorial and try to learn from examples. (well you may find useful [http://diveintopython.org/](http://diveintopython.org/) or [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/) i haven't read them)
[*] Start writing python programs (you need a simple text editor with syntax highlighting + the ability to run a command:  "python -i %(current_file)")
[*] Get familiar with the python doc [http://www.python.org/doc/](http://www.python.org/doc/) (knowing the builtin modules is very important)
[*] If you have some problems then use the interpreter! (most useful builtin functions in this respect: dir(obj), vars(obj), help(obj))
[*] If you need a language reference then use [http://rgruet.free.fr/PQR24/PQR2.4.html](http://rgruet.free.fr/PQR24/PQR2.4.html) insted of the official (it's much more compact)
[*] Look around for useful python libs. i dont know your interests, but some useful modules i use:
[INDENT]
[LIST]
[*]math/matrix: scipy/numpy
[*]3d/game: pygame, pyopengl, pyogre
[*]net: twisted
[*]web: (there are lots of web frameworks ...)
[*]image processing: PIL (=python image lib) 
[*]c/c++ with python: swig, pyrex, boostpython+pyste, ctypes
[*]xml: elementtree (also builtins + lot other ...)
[*]gui: pygtk, wxpython, tkinter ...
[*]... (usually everything you would want to use is available in python)
[/LIST]
[/INDENT]
[*] read others' code (eg. the builtin modules or [http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/))
[/LIST]

---

### Post by krypto_wizard on 2006-01-25
That looks a good help...thanks

---

### Post by earobinson on 2006-01-25
If you have programed before you will pick it up fast, if not it will take some time.

---

### Post by krypto_wizard on 2006-01-25
I have programed in C and partly in Java. Any tips to make it a fast transition ?

If I am stuck at some place, whats the right place to find quick help ?

Thanks

[QUOTE=earobinson]If you have programed before you will pick it up fast, if not it will take some time.[/QUOTE]

---

### Post by nszabolcs on 2006-01-25
[QUOTE=krypto_wizard]
If I am stuck at some place, whats the right place to find quick help ?
[/QUOTE]

[http://groups.google.com/group/comp.lang.python](http://groups.google.com/group/comp.lang.python)
official docs, faq, beginners guide
and again: use the interpreter ( dir(obj) ... )

---

### Post by engla on 2006-01-25
This is a great topic -- I just started two days ago to try to figure out python myself. I've programmed C/C++ but mostly obj-c with cocoa, and from everywhere you hear stuff about python. There seems to be bindings for python everywhere, so finally when I also became curious about gtk I decided I needed python.

I'm basically using the PyGTK 2.0 Tutorial [ [http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html](http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html) ]
And grabbing stuff, reading it through and chaning it to see what works. This has always been how I learn stuff on computers anyway, so it might work.. and I learn gtk at the same time.

I have some questions and problems though:
[LIST]
[*]It took me a lot of time to get used to the bracket-less syntax, and learning to keep track of indenting. I still don't know the best way to do this, I only work with small files/classes, but perhaps gedit is not optimal
[*]However, gedit can be greatly enhanced just by turning on the indenting and line-numbering extensions, of course. Perhaps there are coding- or python-specific extensions to be found?
[*]I managed to make a small drag shelf--something that stores text that you drag to it, and you can drag it from there to everywhere. However, is it not possible to drag images? This doesn't seem to work at all. :-(
[*]Also, a bit off-topic I wonder if there are other tools that might help the gtk-python symbiosis. Is it possible to use glide/something like that with python?
[/LIST]

---

