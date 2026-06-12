---
title: "Screen resolution problems"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ihatejoefitz on 2008-05-05
The best resolution I can get is 1280x800.  I'd like it to go a little higher.  TIA.

x.org configuration,

"Section "InputDevice"
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
"

---

### Post by monkeyslap on 2008-05-05
Type the following at the command line:
sudo dpkg-reconfigure xserver-xorg

You can hit enter for most of the default settings (when in doubt, do that). Toward the end it will ask you for your screen's resolution. For LCDs it's recommended to use the screen's native resolution.

---

### Post by macaholic on 2008-05-05
What kind of graphics card do you have?

---

### Post by Girya on 2008-05-05
I too have screen resolution problems when I run dpkg-... I get to the part about 3 button mouse emulation I get kicked out of the dpkg app and get this complaint from the term.:
> 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080505160251

any ideas on how to get around this? 

thanks Kevin

---

### Post by ihatejoefitz on 2008-05-05
> **macaholic said:**
> What kind of graphics card do you have?

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by ihatejoefitz on 2008-05-05
> **monkeyslap said:**
> Type the following at the command line:
sudo dpkg-reconfigure xserver-xorg

You can hit enter for most of the default settings (when in doubt, do that). Toward the end it will ask you for your screen's resolution. For LCDs it's recommended to use the screen's native resolution.


This only asked me about the keyboard.

---

### Post by ihatejoefitz on 2008-05-05
I found and am reading this... [https://help.ubuntu.com/community/i810]("https://help.ubuntu.com/community/i810")

This allowed me to select higher resolutions, but it doesn't seem to have an effect.

---

### Post by avtolle on 2008-05-05
The old ways don't work with Hardy, as you have learned. sudo dpkg-reconfigure xserver-xorg doesn't do anything for display issues. If you have a copy of the /etc/X11/xorg.conf file from 7.10 (or earlier), there is some information you may insert into the current one by manually editing it. At a minimum, the Horzsync and VertRefresh information needs to be added under "Configured Monitor" under Section "Monitor" which, in my case are:
HorizSync 28-51 (your monitor's specs here)
VertRefresh 43-60 (your monitor's specs here)
; the Section "Screen" needs to be edited to reflect the Modes available, by adding a SubSection "Display" following Section "Device". For me, the following worked (acknowledging my information will be different than yours):
SubSection "Display"
Modes "1024x768"
EndSubSection

Then, after the end of Section "ServerLayout" , I needed to add the following new section:
Section "DRI"
Mode 0666
EndSection

The information necessary came from my /etc/X11/xorg.conf file from 7.10. I did this from the terminal, first did sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #made a backup copy of the existing file
then sudo nano /etc/X11/xorg.conf, and manually edited the file as set out above.

Again, you will need to use YOUR information; there are other things which may need to be added, which I didn't need to do.

HTH.

---

