---
title: "mouse problem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-08-20
I've got a touchpad mouse with three buttons, right click, left click, and scroll.  But for some reason the scroll button works backwords - up moves the page down, and down moves the page up.  How do I fix this?
Thanks

---

### Post by bhadotia on 2008-08-20
I think there should be a invert scroll option in System > Preferences >  Mouse. I can't say exactly coz I'm on win at the moment. See if that option (if it is there ) is checked or you can also take a look at your /etc/X11xorg.conf for some clue to the problem.

---

### Post by SalsaShark on 2008-08-20
There is no invert scroll option in mouse, and I don't know what anything in xorg.conf means.  Any other ideas?

---

### Post by SalsaShark on 2008-08-20
Any ideas?

---

### Post by Gregmond on 2008-08-20
try this:
 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=5335669](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=5335669)

may not be the same, but it may help.
basically look in the xorg.conf file.
back it up before you change anything. its located at:
/etc/X11/xorg.conf

---

### Post by SalsaShark on 2008-08-21
Well, here's the relavent contents of my xorg.conf file:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

I'm assuming I have to add an option to the touchpad.  Any thoughts on how I'd go about doing that?

---

### Post by SalsaShark on 2008-08-30
Sorry guys, I'm going to have to bump this.  I'm still having the problem and it's getting a little annoying.  Any tips?

---

