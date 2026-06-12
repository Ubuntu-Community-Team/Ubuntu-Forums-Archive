---
title: "problem changing screen resolution"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by x88a on 2008-06-24
i discussed this in an earlier thread.
[http://ubuntuforums.org/showthread.php?t=837546](http://ubuntuforums.org/showthread.php?t=837546)
Unfortunately, it still isnt successful.

i cannot make my screen resolution bigger.
my max screen resolution is 1024 x 768

Here are some information:-
i have ATI accelerated graphics driver and it is enabled.
i also have xorg-driver-fglrx, but not xorg-driver-fglrx-dev.

this is my "sudo gedit /etc/X11/xorg.conf" output

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
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
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

i would really appreciate it if someone can help me.
TQ

---

### Post by avtolle on 2008-06-24
Try this from terminal```
gksudo displayconfig-gtk
```and see if your monitor is listed. If it is, then select it.  After closing the application, a new /etc/X11/xorg.conf file will be written to handle the monitor.

I've never used the detect button, so cannot say what it does (my monitor was listed, and after selecting it I got the right resolution and didn't need to pursue it any further).

---

### Post by B61zz13 on 2008-06-24
Go to Applications > System > Preferences > Screen Resolution and change your resolution from there.

---

### Post by x88a on 2008-06-26
> **avtolle said:**
> Try this from terminal```
gksudo displayconfig-gtk
```and see if your monitor is listed. If it is, then select it.  After closing the application, a new /etc/X11/xorg.conf file will be written to handle the monitor.

I've never used the detect button, so cannot say what it does (my monitor was listed, and after selecting it I got the right resolution and didn't need to pursue it any further).

the problem is, i am using a laptop.
So i dont have any monitor to choose.
My Model is "Plug and play"
any more ideas?

tq

---

### Post by x88a on 2008-06-26
anyone can help me??
tq

---

### Post by StevoSn on 2008-06-26
> **x88a said:**
> anyone can help me??
tq

Hey,
I had kind of the same probs with my laptop LCD Display..Anyway, if I pressed the auto detect button the prog always found just the plug&play monitor.

I chose an LCD Display manually. So in my case it was LCD 1440xsomething. so if you know your max screen resolution set it yourself.

try this and see if you can setup a higher res after that..

hope that helps..

---

### Post by cazmatazzz on 2008-06-26
hi i have the same problem, started a thread about it a while ago, even though i still havent figured it out and none of the offered solutions have worked for me, maybe some of the solutions will work for you... good luck! ([http://ubuntuforums.org/showthread.php?t=834528](http://ubuntuforums.org/showthread.php?t=834528))

---

