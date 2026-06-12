---
title: "How to enable scroll wheel?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by techno-wiz on 2008-07-24
How do I enable the scroll wheel on my mouse? It isn't working in nautilus or firefox. This is on a fresh Hardy install.

---

### Post by perlluver on 2008-07-24
```
gksu gedit /etc/X11/xorg.conf
```

Make sure it says either auto under mouse driver, or check to see if it says Option "ZAxisMapping" "4 5" if you have a normal two button mouse with a scroll wheel.

---

### Post by techno-wiz on 2008-07-24
Tried that and it made my mouse completely inoperable.


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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by TBOL3 on 2008-07-25
Could you show us what your xorg file looked like before you had a go with it?

---

### Post by techno-wiz on 2008-07-25
That is what you are looking at in my previous post. I just had xorg autoconfigure to get my mouse working again. It was this way originally and I changed,

driver   "mouse"

to

driver   "auto"

which made my mouse completely non working after a reboot.

---

### Post by techno-wiz on 2008-07-25
Any other suggestions? It used to work when I was using Gutsy.

---

### Post by stevoo on 2008-07-25
try this .... 
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

---

### Post by techno-wiz on 2008-07-25
Well my mouse is still working but not the scroll wheel after trying that. Not sure if it helps but this is a logitech wireless mouse.

---

### Post by bukwirm on 2008-07-25
What model is the mouse? If you got it with a keyboard, the model number might be on the keyboard.

How many buttons does the mouse have, including the Back/Forward buttons and such?

---

### Post by bushda on 2008-07-25
I know this is going to sound dumb, but you are restarting X between updates to xorg.conf, right?

If you don't, it won't update.

---

### Post by techno-wiz on 2008-07-26
It's a logitech cordless mouseman optical. Model number is M-RR63. It has the left/right buttons, scroll wheel which is also a button, and a button on the thumb that used to activate the Back button in a web browser.

Yes, I'm restarting the computer between any changes made to my xorg.conf.

---

### Post by RiceMonster on 2008-07-26
Don't bother restarting, just hit Ctrl-ALt-Backspace after you've made the changes and log back in. That will restart X.

---

### Post by bukwirm on 2008-07-27
You could tale a look at [this thread]("http://ubuntuforums.org/showthread.php?t=532713").

Also, type "xev" in a terminal, place the pointer in the window that comes up, and scroll one step in either direction. A message like the one below should appear in the terminal. Note the button number that comes up in each direction.

```
ButtonRelease event, serial 30, synthetic NO, window 0x1800001,
    root 0x4c, subw 0x1800002, time 1737637005, (34,53), root:(599,78),
    state 0x810, button 4, same_screen YES
```

---

### Post by navlelo on 2008-09-13
My scroll wheel didn't work when I logged on to my fairly fresh Hardy Heron install today (won't scroll, but the scroll wheel button works). It has worked perfectly until today. Yesterday I installed lots of multimedia stuff and played around with config files. There were a bunch of updates today, so it's almost impossible for a newbie like me to backtrack events and find out what has gone wrong. I have not made any manual changes to the mouse settings in xorg.conf, and as far as I can tell they are still at default.

I've tried bukwirms xev tip, and I get no response at all when scrolling the wheel, while all other movements and clicks are reported. I'm not sure what that means. Do I have a hardware problem, or could a software setting give this result? The mouse is 10 years old, so a hardware failure seems reasonable. I opened the mouse and made sure no dust were covering the sensors.
 
Could this be caused in software? If so, where should I start looking?

EDIT: This morning the mouse wheel worked again, and I don't know what happened. I would still like to know what xev outputs; is it unmodified port listening, or are those signals manipulated by settings/software? I tried Google.

---

