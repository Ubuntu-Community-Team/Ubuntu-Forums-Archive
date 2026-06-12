---
title: "Python help.."
date: 2007-02-07
forum: Programming Talk
---

### Post by Nikron on 2007-02-07
I'm trying to create a python program that when executed, checks the last time it was executed and if the last time is either null or more than a second sends ALT + RIGHT to the computer as if it were coming from the keyboard.

Basically, I'm wondering how to send key events from a python program..

Thanks for any help

---

### Post by jblebrun on 2007-02-07
Check out the python Xlib package
[http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13](http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13)

---

### Post by Nikron on 2007-02-07
Oh burn, this is going to be a lot harder than I thought, namely because I really don't know Python.  Thanks for the link

---

### Post by Nikron on 2007-02-07
Ohh nice, figured out how to do it without connecting to the x server, or even making a class

import os
os.system("/usr/bin/xvkbd -xsendevent -text '\[Alt_L]\[Left]'")

---

### Post by Wybiral on 2007-02-07
Classes at least are a good thing to know, just for future reference... If you don't know any OOP at all, at least learn to use classes... It helps a lot.

---

### Post by Nikron on 2007-02-08
> **Wybiral said:**
> Classes at least are a good thing to know, just for future reference... If you don't know any OOP at all, at least learn to use classes... It helps a lot.

Well.. I kinda made it object oriented but not really, since it's such a small program...

It works though

```

import os
import time

class altLeftSticky:
	read = open("/home/nikron/General/lasttime.txt",'r')

	def sendAltLeft():
		"""Sends ALT+LEFT to the X server"""
		os.system("/usr/bin/xvkbd -xsendevent -text '\[Alt_L]\[Left]'") 

	def wtime():
		return str(time.time())


	last = float(read.read()) + 1

	if time.time() > last:
		sendAltLeft()
		write = open("/home/nikron/General/lasttime.txt",'w')
		write.write(wtime())
		write.close()

```

My first python program

---

