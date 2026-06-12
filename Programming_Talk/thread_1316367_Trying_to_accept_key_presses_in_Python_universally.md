---
title: "Trying to accept key presses in Python universally"
date: 2009-11-05
forum: Programming Talk
---

### Post by billdotson on 2009-11-05
Ideally what I would like to do is be able to have the little game I am working on be able to be run on any machine that has standard python modules on it. For the initial method of getting key presses to work the msvcrt.dll (or whatever it is) in Windows was very simple.

The only way I have seen to do it in Linux (or any system that uses a POSIX-style terminal, tty) is the following (I found this on some forum):

```

import sys
import tty
import termios

i = sys.stdin.fileno()
o = sys.stdout.fileno()

backup = termios.tcgetattr(i)

def loop():
    while 1:
        ch = sys.stdin.read(1)
        print "->%s"%ch
        if ch == 'q':break

try:
    tty.setraw(i)
    loop()
finally:
    termios.tcsetattr(i, termios.TCSADRAIN, backup)

```

I have not tested it yet but I have tried to look and see what it does exactly. However, when trying to find what exactly sys.stdin.read(1) does I have noticed the python documentation on the modules in a lot of sys have no description at all. If you go to the stdin or stdout area of the sys page it has absolutely nothing particular to each one. All it does is give a paragraph about the three in general and has nothing about the 'read' or 'readline' modules.

Is someone writing some code just supposed to magically know how it works? If I want to know what sys.stdin.read(1) does I should be able to figure it out by looking at the documentation. It seems pretty straightforward that sys.stdin.read reads standard in, but how would I know what the argument '1' does if the documentation says absolutely nothing about it, even going as far as not saying that 'read', 'readline', or fileno() is a part of sys.stdin? 

If any of my information is incorrect (there is some place in the documentation where it is explained better, or in full detail) please forgive me). As much as I have looked though it seems as if I am left in the dark as to what to do.

This is a side note, but I went to the POSIX manuals to see exactly what tty was and all I got was a page saying: "The tty utility writes to the standard output the name of the terminal that is open as standard input." That barely makes any sense to me when I try to consider the usefulness of what it does. What exactly is "the name of the terminal"?


Like I said, I would ideally like a solution that would work for Windows and Linux (and OS X I suppose but I don't own OS X so only a very small amount of people, if any, would ever use it), but if that isn't possible I guess I could use that bit of code above for Linux and getch and mscvrt for Windows (what I have already implemented).

Thanks.

---

### Post by nvteighen on 2009-11-06
The issue is that you're using a module you shouldn't. Use ncurses, not termios! [http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

The ncurses library is written in C and is the preferred way to create so-called TUIs (Text User Interfaces) and perform any kind of high-level terminal manipulation. ncurses is a reproduction of the old "curses" library (hence the name: ncurses = "new curses") and that's why it uses a somewhat odd API. There are alternatives, but I don't remember them having a Python binding and neither ever heard about someone using those.

ncurses is meant for UNIX/Unix-like OSs, but I'm sure it has been ported to Windows.

---

### Post by sheep1 on 2009-11-06
sys.stdin, sys.stdout, sys.stderr are all File Objects. Look up the documentation on File Objects for information about read() and readline().

---

