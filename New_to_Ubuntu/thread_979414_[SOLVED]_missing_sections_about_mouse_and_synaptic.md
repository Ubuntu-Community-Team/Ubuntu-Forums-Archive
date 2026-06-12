---
title: "[SOLVED] missing sections about mouse and synaptic in xorg"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-11-11
I'm a bit curious how my mouse and touchpad are working without having a section in my xorg.conf. Here's what's in it right now.

```

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

```

The mouse and touchpad are working fine but I'd like to turn off the touchpad. So the question I have is: **does anyone know why I might be missing the sections about mouse devices and how I could get them back (so I can enable SHMConfig and turn of the touchpad)?**

PS: I've run dpkg-reconfigure -phigh xserver-xorg but all that did was take out the sections about the fglrx driver.

---

### Post by cariboo on 2008-11-11
Mouse and keyboard are no longer configured in xorg,cong. There shoud be a menu item to control your touchpad. Look for System-->Preferences-->Touch pad.

Jim

---

