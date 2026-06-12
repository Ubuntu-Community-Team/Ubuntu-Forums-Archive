---
title: "touchpad"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by chrishj82 on 2008-08-16
Hi!

First time i try linux. I have a problem with my touchpad going completly crazy. It either doesent move at all or go really looney jumping around the screen clicking like crazy. When i use a usb mouse it works fine.  Can anybody help me with this? I allready tried to fix it in xorg.conf but this diddnt solve anything

I have a xps 1530 (new). I have synapicts pad i think.

Kind regards

Chris

---

### Post by bhadotia on 2008-08-16
Dell hmm.. my friends with these pcs are also having the same problem in linux. I think you should try installing gsynaptics to tweak your touchpad. Edit the xorg.conf file after installing and log out and log back in, to use gsynaptics. Also try checking the settings in the Mouse menu in Syste>Preferences.

Good luck!

---

### Post by chrishj82 on 2008-08-16
Hi!

Thanks for you reply. Yeah I tried to do this but i seem to not be able to edit the xorg correctly.
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMconfig"		"true"

I tried both "true" and "on" but i still cant get acsess to the config tool. This is really the only thing thats doesent work. I had alot more problems when i downgraded from vista to xp.

Kind regards

Chris

---

### Post by chrishj82 on 2008-08-16
Ok.. I fixed the zorg problem

But the touchpad still is jumping around like crazy..
Anobody know what to do??

Regards

Chris

---

