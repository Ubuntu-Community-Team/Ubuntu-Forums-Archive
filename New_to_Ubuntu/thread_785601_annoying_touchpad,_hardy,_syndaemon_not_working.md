---
title: "annoying touchpad, hardy, syndaemon not working"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by raequin on 2008-05-07
Hi.  I have an Acer laptop.  When I type, the touchpad will often cause a click where the pointer is, so the cursor ends up jumping around.

I have tried many things, the only solution so far is to use the touchpad on/off button (fn+f7) on my laptop.  Even System+Preferences+Mouse+Touchpad->disable mouse clicks with touchpad has no effect.

I have edited xorg.conf and run syndaemon without result.  Here is the touchpad section of that file.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"on"
#	Option		"MaxTapTime"		"0"
EndSection

I commented out the maxtaptime, because it had no effect.

I have run syndaemon both with and without options --- no effect.

Thanks for helping me get this working.

One other option would be a keyboard shortcut that I can access from the home position (Emacs has spoiled me).

 * edit: Vertical scrolling is not working either.  That would be nice.

---

### Post by raequin on 2008-05-08
* bump *

It would be nice to get this resolved.


ps - Is 12 hours too short a time to expect a response?

---

### Post by raequin on 2008-05-09
* bump ?

---

### Post by raequin on 2008-05-10
Guess what?  * bump *

---

### Post by fresta on 2008-09-17
I don't have a solution unfortunately, I can just confirm that it doesn't work for me either. Used to work fine up to Gutsy so something has happened in Hardy.

---

### Post by tone33 on 2008-11-05
I have issues with the touchpad on my acer as well.  My issues are slightly different than yours, but I have not had any response after several posts here.  not sure if there is a better forum to post questions about acer touchpad/ubuntu issues...

---

