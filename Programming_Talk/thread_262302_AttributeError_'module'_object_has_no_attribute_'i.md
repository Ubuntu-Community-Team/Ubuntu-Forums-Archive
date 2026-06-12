---
title: "AttributeError: 'module' object has no attribute 'initscr'"
date: 2006-09-21
forum: Programming Talk
---

### Post by ironfistchamp on 2006-09-21
Basically that is the error whenever I try to initiate curses when using pycurses. I don't know why it is doing this or what is going on. 

```

#! /usr/bin/env python

import curses

scr=curses.initscr()
curses.noecho()
curses.cbreak()
scr.keypad(1)
scr.addstr("Hello World with Curses")
refresh()
scr.getch()
curses.nocbreak()
scr.keypad(0)
curses.echo()
curses.endwin()

```

That is what I am using and this is the output I get

```

Traceback (most recent call last):
  File "./curses.py", line 3, in ?
    import curses
  File "/home/dstamp/DansGame/curses.py", line 5, in ?
    scr=curses.initscr()
AttributeError: 'module' object has no attribute 'initscr'

```

Any help would be great. Thanks

Ironfistchamp

---

### Post by Tomosaur on 2006-09-21
Don't give your python file the same name as the module you're trying to import, it can lead not only to confusion but also to errors. Try renaming your pyton file to cursesTest.py or something. I think what is happening is that your code is looking for the initscr() method from within your own file.

---

### Post by ironfistchamp on 2006-09-21
Haha that was a stupid thing for me to do :p  Thanks I shall see what happens this time.

Thanks again

Ironfistchamp

EDIT: Excellent it works. Thanks alot :D

---

### Post by yanom on 2009-12-10
> **Tomosaur said:**
> Don't give your python file the same name as the module you're trying to import, it can lead not only to confusion but also to errors. Try renaming your pyton file to cursesTest.py or something. I think what is happening is that your code is looking for the initscr() method from within your own file.

Thanks alot, I was having the same problem.

---

