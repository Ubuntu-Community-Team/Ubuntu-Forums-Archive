---
title: "[HOWTO] MX510 Gutsy Gibbon"
date: 2008-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Enfenion on 2008-01-21
First of all, run
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf~backup
```
If your system hangs, you can run
```
sudo cp /etc/X11/xorg.conf~backup /etc/X11/xorg.conf
```
to get x back.

**1. Changing xorg.conf:**

```
cat /proc/bus/input/devices
```
and find the one with:
N: Name="Logitech USB-PS/2 Optical Mouse"
look at "Handlers", f.ex.
```
H: Handlers=mouse1 event4
```
note the number after event, (i.e. event4)

in xorg.conf:
```
gksudo gedit /etc/xorg.conf
```

change
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
to
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event4"
	Option		"Protocol"	"ImPS/2"
	Option		"Buttons"	"10"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
(Changed Driver to "evdev", changed "Device" to "/dev/input/[THE EVENT FROM EARLIER]" added Option "Buttons" "10")

Restart x by pressing [Ctrl]+[Alt]+[Backspace] at the same time, and everything should work. If you can't get back in to gnome, you could revert from backup as stated above and run
```
sudo /etc/init.d/gdm restart
```
If everything works continue to the next step.

**2. Mapping the keys**
Install xvkbd and xbindkeys
```
sudo apt-get install xvkbd xbindkeys
```
and make the ~/.xbindkeysrc file:
```
gedit ~/.xbindkeysrc
```
write
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"/usr/bin/gnome-terminal"
  b:8
```
and save.
(enables back and forward. the last two lines makes the "logitech button" or whatever start a new terminal)
and then run
```
xbindkeys
```
Check if everything works.

Then make xbindkeys start automatically:
System -> Preferences -> Sessions -> Add -> xbindkeys

---

### Post by Enfenion on 2008-11-09
This is MUCH easier in 8.10:

With clean install:

```
nano .xbindkeysrc
```

```
"/usr/bin/gnome-terminal"
b:10
```

And start xbindkeys as in the tutorial above.

---

