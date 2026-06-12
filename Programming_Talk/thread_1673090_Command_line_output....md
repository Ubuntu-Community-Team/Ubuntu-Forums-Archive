---
title: "Command line output..."
date: 2011-01-21
forum: Programming Talk
---

### Post by evildork on 2011-01-21
Couldn't think of a more specific title.

How do programs like vim, Nethack and lynx use the command line to display their interface without it being outputted into the command line? 

What is that called? And can I do it with my python programs?

---

### Post by hakermania on 2011-01-22
I don't get you.... Do you want no output to be displayed to the command line? If yes, then try using > /dev/null or 2> /dev/null after the command...e.g.
gedit > /dev/null

---

### Post by m_duck on 2011-01-22
> **evildork said:**
> What is that called?
[Ncurses](http://en.wikipedia.org/wiki/Ncurses)?
> **evildork said:**
> And can I do it with my python programs?
I imagine the answer is yes. Googling ncurses and python brings results, though I know very little python and so can probably not be any more help than this.

---

### Post by TwoEars on 2011-01-22
> **evildork said:**
> Couldn't think of a more specific title.

How do programs like vim, Nethack and lynx use the command line to display their interface without it being outputted into the command line? 

What is that called? And can I do it with my python programs?

Ncurses.

In Python, you can use [curses]("http://docs.python.org/library/curses.html")

---

### Post by cgroza on 2011-01-22
There is a toolkit called curses for python and ncurses for C++ I think. You will need to learn it if you want to use it. It basically does the same thing like a GUI toolkit, except in a different way and for a command prompt.

---

### Post by evildork on 2011-01-22
Thanks guys, that's what I was after. Can't remember the last time I couldn't get an answer out of Google; it's tricky when you don't know what you're asking.

---

