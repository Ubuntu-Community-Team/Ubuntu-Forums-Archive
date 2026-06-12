---
title: "Translating Keystrokes in Python"
date: 2006-10-10
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-10
Hello again!

Is there a way to detect and translate keystrokes in a python TEXT MODE program?

i.e. I want to have a text menu that says:

Menu: 
1. sdfljsdlfjs
2. slfjsdljf
3. Quit

I don't want to have to press enter after making the selection. I just want to press 1, 2, or 3 and have the program respond accordingly.

Thank you.

Best,
Tom

---

### Post by po0f on 2006-10-10
thomasaaron,

You can use [curses](http://docs.python.org/lib/module-curses.html) to do this.

---

### Post by thomasaaron on 2006-10-10
OK, after quite a bit of research, I've come up with this little subroutine to detect keystrokes, which is based on curses.

I'd like to turn it into a function and call it from another program in order to allow me to just press the number of a menu item and have the program respond accordingly.

The problem is, if I print a menu on the screen, and then call this function, it will cause my screen to blank out.  It still detects keystrokes, but what good is that if you can't see the menu?

So, I have two questions:
1. Is there an easier way to detect keystrokes in TEXT MODE than using curses?
2. If not, how can I do this so that it does not blank out the menu screen?

Thanks,
Tom

[PHP]#!/usr/bin/env python

#keystroke.py

loop = True

import curses

print "This is the first line"
print "This is the second line"
print "This is the third line"


stdscr = curses.initscr()


curses.noecho()
curses.cbreak()

while loop:
    c = stdscr.getch(0,0)
    d = c-48
    print d


curses.nocbreak()
curses.echo()
curses.endwin()
[/PHP]

---

### Post by ghostdog74 on 2006-10-10
check this [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/134892]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/134892")

---

