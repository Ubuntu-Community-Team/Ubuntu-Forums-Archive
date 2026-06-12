---
title: "help with xorg.conf"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by alex-santos on 2008-08-31
Hi everybody

Can anybody explain where is the the rest of configuration. This is all what I have in xorg.conf where is Driver, BoardName,  from Section "Device" section for example, other part also missing like in Section "Monitor" Modeline and Options.


Much appreciate. 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ie"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by kerry_s on 2008-08-31
xorg has changed, it is now automatically done. check your /var/log/Xorg.0.log

you can still put any settings you need manually.

---

### Post by mali2297 on 2008-08-31
As has been said, the default configuration method has changed. Do you have a specific problem that you need help with?

---

### Post by Toshibawarrior on 2008-09-01
Hey mali2297...I'm having a problem with my xorg.conf...It's almost exactly the same as alex-santos' one and I need to use Randr for using my external monitor as an extension and not a clone/mirror. 

The Randr tutorials talk about some "virtual" desktops and stuff like that, which is supposed to be listed somewhere in the xorg file...But my xorg.conf's video sections are flat. They just say "Configured Monitor" and so on...

Could you help me understand [_this tutorial_]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). It ask for some things that are not listed on my xorg, and the command it gives for making a "new" xorg.conf doesn't work for me...It just leaves the xorg as it is and makes a backup inside /etc/x11/...

Any help is greatly appreciated! ;)

---

### Post by mali2297 on 2008-09-01
> **Toshibawarrior said:**
> Hey mali2297...I'm having a problem with my xorg.conf...It's almost exactly the same as alex-santos' one and I need to use Randr for using my external monitor as an extension and not a clone/mirror. 

The Randr tutorials talk about some "virtual" desktops and stuff like that, which is supposed to be listed somewhere in the xorg file...But my xorg.conf's video sections are flat. They just say "Configured Monitor" and so on...

Could you help me understand [_this tutorial_]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). It ask for some things that are not listed on my xorg, and the command it gives for making a "new" xorg.conf doesn't work for me...It just leaves the xorg as it is and makes a backup inside /etc/x11/...

Any help is greatly appreciated! ;)

First, have you tried continuing with [First discover what we have](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#First_discover_what_we_have) in the tutorial? The default xorg.conf might work fine.

---

### Post by Toshibawarrior on 2008-09-01
Yes I did. My external monitor, which is a Panasonic TV is recognized as a mirror or a clone of the Laptop's monitor...

I'm currently searching for some other threads on the web that might help me fix my xorg. My xorg.conf is:
```

# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

I'm very frustrated here. I read that I should modify some of the xorg.conf's sections for xrandr to correctly configure it. :(

---

