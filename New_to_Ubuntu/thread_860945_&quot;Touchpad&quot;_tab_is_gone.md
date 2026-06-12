---
title: "&quot;Touchpad&quot; tab is gone"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Kuronin on 2008-07-16
Hi, new to Linux here, as in using it for the first time ever starting last night. I'm getting a hang of it, but this one I can't just seem to get to go.

When I loaded up Hardy, I had access to the "Touchpad" tab in the mouse settings. I ended up installing a few more drivers, nothing to deal with a touchpad, then suddenly it was gone. I've tried the whole "SHMConfig" attack plan, and it was a no go, still doesn't recognize it as being there.

I've tried reinstalling, deleting and installing, etc., Gsynaptic, and that doesn't make a lick of difference either.

I have a Satellite A215-S4757 if that helps too (ALPS touchpad)

Here's my xorg.conf

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
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
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
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

So, any idea what this lowly noob needs to do?

(Btw, I'm actually having a great time just debugging and getting everything to work with this, I can't believe I waited 6 years to get into Linux lol)

---

### Post by someonestolemyname on 2008-07-18
I'm glad your into Linux!

Regarding your problem: have you restarted X since you tried the SHM config thing? It's Ctrl-Alt-Backspace or just restart the computer. That should make it go into effect.

A Synaptics search shows the program 'tpconfig' which looks like it could help you. I think the issue is the ALPS touchpad, rather than Synaptics.

gSynaptics doesn't add that dialog, it creates a new one under System > Preferences > Touchpad. It offers everything the other ialog does and more.

This shouldn't be too bad, Linux seems to have no problems with touchpads.

Good luck!
Daniel

---

