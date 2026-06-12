---
title: "[SOLVED] screen display fit"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-06-01
This is a small issue but since I upgraded to Hardy, my desktop display appears to extend just a slight bit too far to right so, for instance, the shutdown button is 1/2 off of the screen.
This is new as of the upgrade.  The video card is nvidia and I'm using the proprietary drivers.
Any ideas how to fix this?  (it isn't a critical issue, just a small cosmetic annoyance)
thanks

---

### Post by SunnyRabbiera on 2008-06-01
In a terminal type in gksu displayconfig-gtk
it might help

---

### Post by flyingsolo on 2008-06-01
Thanks, but no improvement--I have choices of nvidia or nv drivers and it would seem the nv is most appropriate since card is Geforce 4 (older Dell).  Still the shutdown button and trash are just visible on screen edge.

---

### Post by Confazed on 2008-06-01
I used this method when I plugged my laptop into another screen and my resolution was too high:

sudo gedit /etc/X11/xorg.conf

scroll down to the screen section and add a virtual screen that is exactly the resolution of your display (should be smaller than the current setting).

It should look something like this (the line I added is in bold):
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
		**Virtual 	1024 768**
	EndSubSection
EndSection

Then I just reset gnome with control+alt+backspace and logged back it.

---

### Post by flyingsolo on 2008-06-01
OK--mea culpa!  I just hit the 'auto adjust' button on the bottom of the monitor and, voila! Fixed.
Sorry for wasting people's time.  Probably someone at home misadjusted the screen accidentally when pushing the on/off of the LCD screen.

---

