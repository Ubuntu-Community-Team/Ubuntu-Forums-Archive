---
title: "[Python] Making terminal enhancements/graphics"
date: 2011-03-12
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-12
So, I'm building a module based on the things I've learned in Python and think are cool. I'm doing it for strictly educational purposes, would anyone like to add anything?

```

"""SmashIndex terminal improvements:
Note: This project was started to show
programmers the importance of
documenting functions and as a means
to improve my own understanding of Python

functions include:

cls() - Clears the terminal
box(x, y) x = Creates a box based on text given
    for x. length is y (It is a number)"""

import os

def cls():
    """Function clears screen returning a
blank line to avoid the common
Windows '0' return"""
    os.system("cls")
    return "\n"

def box(x, y):
    """Returns value given for x in a box
with lengths of y box("text", 2)"""
    if x * 0 == 0:
        return "Sorry x must be text in ''"
    if y % 2 == 0:
        return "Sorry y must use an odd length"
    if y < 5:
        return "Sorry y must use a number > 5"
    x = x + " "
    print x * y
    print x + ((len(x) * (y - 2)) * " ") + x
    z = (len(x) * y)
    a = (len(x) * 3)
    a = (z - a) / 2
    print x + (a * " ") + x + (a * " ") + x
    print x + ((len(x) * (y - 2)) * " ") + x
    print x * y
    return "\n"

```

---

### Post by wmcbrine on 2011-03-13
os.system('cls') won't work in Ubuntu unless you change it to "clear", but even then, you're spawning a whole new shell and executable just to clear the screen. That kind of makes sense for a batch file or shell script, since that's mostly what they do anyway, but IMHO it's overkill for a Python script.

```
import sys

def cls():
    sys.stdout.write('\x1b[2J\x1b[H')
```

This will work on most common terminal types. I dunno about Windows.

Well, at least, that's how I'd do it if I wasn't using curses, which is probably the way to go here. But curses does have some overkill issues of its own...

---

### Post by ki4jgt on 2011-03-13
> **wmcbrine said:**
> os.system('cls') won't work in Ubuntu unless you change it to "clear", but even then, you're spawning a whole new shell and executable just to clear the screen. That kind of makes sense for a batch file or shell script, since that's mostly what they do anyway, but IMHO it's overkill for a Python script.

```
import sys

def cls():
    sys.stdout.write('\x1b[2J\x1b[H')
```

This will work on most common terminal types. I dunno about Windows.

Well, at least, that's how I'd do it if I wasn't using curses, which is probably the way to go here. But curses does have some overkill issues of its own...

Thanks. . . In Ubuntu it doesn't clear the terminal at all (os.system) It merely pushes everything up and out of sight. Windows however this does wonderfully (Except for the returned 0. That gets annoying, because it'll display everything you print to it and then you see an eye sore when you see the zero at the top of the screen. I can't conplain though, I didn't write the os module and it's pretty nifty. I'll try your code though.

I'm also about to put a circle in there too. :-)

---

