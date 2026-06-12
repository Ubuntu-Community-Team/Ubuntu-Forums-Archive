---
title: "Yet another idiot asking about &quot;dual-monitors&quot;"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by iamfletch on 2008-06-16
Im running a dell dimension 5150, with a ATI radeon x1800 256MB graphics card instead of the original one. I have a new 22" DVI wide-screen monitor (1680x1050), plugged into DVI slot and i have and old 19" VGA monitor(1280x1024), plugged into DVI using a converter.

Im running ubuntu hardy 8.04, im trying to use the Xinerama to set up dual monitors, with no luck. I get an error on boot that makes me run in the "low-graphics" mode.

heres my xorg.conf file:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"0 Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver		"fglrx"
	Screen      	0
	Option "DDCMode" "True"
	Option "MonitorLayout" "TMDS,TMDS"
EndSection
Section "Device"
	Identifier	"1 Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver		"fglrx"
	Screen      	1
	Option "DDCMode" "True"
	Option "MonitorLayout" "TMDS,TMDS"
EndSection

Section "Monitor"
	Identifier	"0 Configured Monitor"
EndSection
Section "Monitor"
	Identifier	"1 Configured Monitor"
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Monitor		"0 Configured Monitor"
	Device		"0 Configured Video Device"
EndSection
Section "Screen"
	Identifier	"1 Default Screen"
	Monitor		"1 Configured Monitor"
	Device		"1 Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "0 Default Screen"
	Screen		1 "1 Default Screen" RightOf "0 Default Screen"
	Option		"Xinerama" "true"
EndSection

```

Any ideas?

---

### Post by iamfletch on 2008-06-16
$ fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

im sure this is supposed to display both screens, and also i cant understand why mesa is showing up!

any help yet?

---

### Post by Sef on 2008-06-16
Moved to Absolute Beginners.

---

