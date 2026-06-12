---
title: "Progamming Environment"
date: 2010-02-07
forum: Programming Talk
---

### Post by cprofitt on 2010-02-07
I would like to get some recommendations for a programming environment or tool set to use.

I intend to program in the following languages:

C
Python
Lisp

I would like the ability to make graphical and command line programs.

Is there a good environment for doing so? Is there a good set of tools that work well together?

Thanks

---

### Post by LKjell on 2010-02-07
A good text editor like vim and the gnome-terminal to compile and run programs is a good start. You learn much more since an IDE gives you too much for free.

It is like learning math you do calculate it by hand first. Ever seen a first grade pupil using calculator?

---

### Post by Ravenshade on 2010-02-07
Hm I tend to work through hard coding (hence gedit and g++ for compiling my c++ code) but Code::Blocks was quite efficient for me.

---

### Post by Ferrat on 2010-02-07
I myself really like Geany, more of an advanced text editor really with project capabilities and a few small things making it easier to use than just a text editor :)

---

### Post by CptPicard on 2010-02-08
If you want everything on the same "platform", it's either Emacs or Eclipse (CDT+PyDev+cusp). Probably the latter for you.

There's nothing wrong with IDEs; in learning, guiding towards correct solution, instant feedback on error and constant reinforcement of what is correct is a very efficient learning strategy. The thing is that IDEs do not hide anything from you (with the possible exception of C-project build tools -- but you'll be able to learn them when you need them, and there is no reason to ignore what you get from IDEs just so that you can get stumped by project management), and they deliver very much in the guiding, feedback and reinforcement departments... when learning a new library, I still find API tooltips remarkably valuable :)

In languages like Java where IDE refactoring support is very strong, the case for an IDE is even greater, as you learn to do OOP design much faster when you get suggestions of what is available, don't have to retype everything manually when you are experimenting, and when you do run into problems, the IDE is capable of telling you what trivial things it is capable of fixing on its own.

---

### Post by matthew.ball on 2010-02-08
You might be interested in emacs.

You can get modes for the 3 mentioned languages (C, Python and Lisp), multiple buffers, in-built terminal, make, there are numerous more, plenty of which I have no experience with. All available with a few key presses - the most common of which usually offer an auto-complete.
I've found it to be pretty useful myself, it does take some effort to learn, but the reward has been well worth it in my case.

As far as graphical programming goes, all I could think of is something like Glade for C and Python (write the graphical forms with Glade and then import the generated code).

I have no idea about Lisp, but some googling has returned wxCL ([http://www.wxcl-project.org/language/en/](http://www.wxcl-project.org/language/en/)).

wxPython (and wxGlade) are also from the wx-family which you may be interested in.

I have no experience with it personally, but there probably is a wx binding for C out there.

Otherwise it is more commonly associated with C++ as far as I know. I personally believe the wx-library would be a sufficient enough reason to become more familiar with C++ if you already know C.

---

