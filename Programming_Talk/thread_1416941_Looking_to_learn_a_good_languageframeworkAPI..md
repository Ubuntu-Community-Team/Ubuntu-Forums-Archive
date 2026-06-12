---
title: "Looking to learn a good language/framework/API."
date: 2010-02-26
forum: Programming Talk
---

### Post by RussianVodka on 2010-02-26
Hey everyone. I'm wondering if anyone has any recommendations for a good language or API for me to learn.

I'm a pretty competent Java programmer ([here is my latest project]("http://epoblaguev.com/?page=Projects/graphCalc.php&subNav=Projects/navBar.php")), but I've been growing weary of it as of recent. It's a lot of small things that make me dislike it, like the inability to use pointers/pass by reference, the amount of typing it takes to get anything done, and recently it's been feeling very locked down and hard to control. If you've used VB for any large project, you've probably experienced something similar.

At the same time I can't stop using it because it's the only language I can find that's both easily portable across platforms, and has a decent GUI library (or the best one I've been able to find so far). And also there is NetBeans, which is a great Java IDE.

I like programming in python. It's fun and easy. On top of that the software runs on any platform with a python interpreter. The downside is that all the IDE's I've used feel sub-par. And I've yet to use a python GUI library that doesn't make me want to head-butt someone in the face.

I might give C++ a try. I know the language enough to get around in it, but I have no idea how to build GUI's in it, or which IDE's are good, or how to make sure the things I write will work on different platforms. As far as I remember, it's also pretty high maintenance, what with the lack of garbage collectors and what not.

So, any advice?

---

### Post by nmccrina on 2010-02-26
> **RussianVodka said:**
> like the inability to use pointers/pass by reference

Lol, more like the inability to use anything *but* pointers/pass by reference!

Learn [brainf***k]("http://en.wikipedia.org/wiki/Brainfuck"). :D

Oh, and if you do C++ you can use Qt for GUI's. I would say it's the closest in feel (programming-wise) to Swing, and I believe it does garbage collecting for you. It also has a good IDE, QtCreator.

---

### Post by Some Penguin on 2010-02-26
Java is call-by-value, not call-by-reference... and it doesn't have pointers to pass.

C++ isn't cross-platform, since it doesn't define type sizes, endianness, or even things like how to fork new processes.  Best you can do is look for libraries for which people have already put in the non-trivial effort for cross-platform behavior, and watch your own code for trouble spots (like relying on a machine's representation of particular types).

---

### Post by RussianVodka on 2010-02-27
So I just tried using C++, and I was reminded of all the things I don't like about it. It's a lot of small annoyances that I don't have to deal with in Java, like locations of functions mattering, and how when you're reading from a file, depending on which OS you're using the behavior is completely different. I think I'll pass on it for now.

What about C#? It looks like a less locked down version of Java. Would the Mono project allow me to write cross platform applications?

---

### Post by matthew.ball on 2010-02-27
You have already said you don't mind Python. There's a really nice cross-platform toolkit - [wxWidgets]("http://www.wxwidgets.org/") - which has a Python binding available - [wxPython]("http://www.wxpython.org/").

If you're after a GUI designer there's [wxGlade]("http://wxglade.sourceforge.net/").

After a while I found the GUI designer approach pretty tedious.
These days, if I'm programming I'll tend to just use [emacs]("http://www.gnu.org/software/emacs/") and a [makefile]("http://www.gnu.org/software/make/").

Edit: If you're interested in using emacs for Python development, I just found [this]("http://jesselegg.com/archives/2010/02/25/emacs-python-programmers-part-1/") series. It seems pretty interesting.

---

