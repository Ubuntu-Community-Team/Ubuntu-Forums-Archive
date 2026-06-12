---
title: "4 Button Mouse."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by BlahMan_of.Doom on 2008-06-03
I have a 4 button mouse, a Microsoft Comfort Optical Mouse 3000 to be exact. Whenever I click Mouse4 (the button on the left side), my mouse freezes in Ubuntu. Is there anyway I can make Mouse4...usable?

EDIT: That's weird..now it only seems to be breaking Ubuntu when I'm in a wine application ( i.e. Warcraft III)

---

### Post by BlahMan_of.Doom on 2008-06-03
Wow..this is weird. I found this thread, and came up with this code there (props to whomever posted it)
[http://ubuntuforums.org/showthread.php?t=252467](http://ubuntuforums.org/showthread.php?t=252467)
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"8"
	Option		"ButtonMapping"		"1 2 3 8 6 7"
EndSection
```
My mouse is USB, not PS/2, so would I change it to ExplorerUSB?

---

### Post by Shazaam on 2008-06-03
Nope. "ExplorerPS/2" is fine.

---

### Post by BlahMan_of.Doom on 2008-06-03
Thanks, it works.

---

