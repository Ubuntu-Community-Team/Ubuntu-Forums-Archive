---
title: "Python: Break loop on keypress."
date: 2010-06-20
forum: Programming Talk
---

### Post by Karakh on 2010-06-20
Is it possible to break a loop on pressing the space key?

---

### Post by Martin Witte on 2010-06-20
Does [this thread]("http://ubuntuforums.org/showthread.php?t=304833") helps?

---

### Post by wmcbrine on 2010-06-20
The simplest way to do a keyboard-interruptible loop is like so:

```
try:
    while True:
        pass # do the loop here
except KeyboardInterrupt:
    pass # do cleanup here
```

However, this is only interruptible by ^C, not space... and it (mostly) doesn't work under Windows. :(

---

### Post by Bachstelze on 2010-06-20
It depends what exactly you mean by "break". If you mean "instantly terminate", then no. If you can wait until the next loop iteration, then maybe. You'd need a thread that sets some global variable to True when the space key is pressed (maybe with dbus?), and the normal worker thread where you would add a [font=monospace]while not space_pressed:[/font] loop.

---

### Post by ssam on 2010-06-20
here is a minimal example with curses

```

#!/usr/bin/env python
import curses

def main(win):
	win.nodelay(True) # make getkey() not wait
	x = 0
	while True:
		#just to show that the loop runs, print a counter
		win.clear()
		win.addstr(0,0,str(x))
		x += 1
		
		try:
			key = win.getkey()
		except: # in no delay mode getkey raise and exeption if no key is press 
			key = None
		if key == " ": # of we got a space then break
			break

#a wrapper to create a window, and clean up at the end
curses.wrapper(main)

```

it takes a bit of extra code to set up, but it works.

also using curses will mess with all the input and output. you can't use print anymore, you have to use addstr and give a position.

---

### Post by ssam on 2010-06-20
or try this:
[http://code.activestate.com/recipes/134892-getch-like-unbuffered-character-reading-from-stdin/](http://code.activestate.com/recipes/134892-getch-like-unbuffered-character-reading-from-stdin/)

---

