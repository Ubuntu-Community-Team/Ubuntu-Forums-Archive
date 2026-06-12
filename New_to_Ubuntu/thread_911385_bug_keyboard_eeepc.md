---
title: "bug keyboard eeepc"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by trigsenior on 2008-09-05
hello,

I think i have found a bug. I have an eeepc , the keyboard for some 
reason keeps  adding a num pad to the keyboard. The config is correct as 
in terminal it works and the login gdm the keyboard is fine. When gnome 
starts the keyboard is messed up =( 

this is my sudo nano  /etc/X11/xorg.conf  

```

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"CoreKeyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
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

thanks

---

### Post by trigsenior on 2008-09-05
any ideas :confused:

thanks

---

### Post by trigsenior on 2008-09-07
bump , it went and came back anyone :(

---

### Post by poltak on 2011-04-13
Sorry to be bumping an ancient thread, but I encountered the same problem on my Eee PC and it made me EXTREMELY frustrated, but I managed to find a simple solution today. Therefore, I thought I'd like to answer it here as this was the first result on Google after searching "eeepc ubuntu keyboard" and it never went properly answered (like all the other threads on this issue). Also, this was on a fairly new install of 10.10.


**Skip this section if you just want the solution:**
*Anyway, after a bit of searching I tried the method which requires you to install an app called "mouseemu". Anyway some threads said to install this app, others said to uninstall this app. Both to fix the same issue ](*,) Okay, so I played around with it for a bit, and realised that if I installed this, it would make my keys work for a bit, then it would stop working until I uninstalled it, which it would then work for a limited time and then stop... Very strange, but anyway this solution only proved a partial solution for me.*


Anyway, at this time I had mouseemu fully uninstalled from my system, as it wasn't helping. So I decided to play around with some keys and finally realised that all that I needed to do to fix this issue was:
 [SIZE="4"]**press Fn + Insert(NumLock)**[/SIZE]    (above backspace)
Yes... apparently this whole thing was caused by NumLock to be infinitely turned on after plugging in a usb keyboard...


So it took me a few hours to find this infuriatingly easy fix for this crippling problem, so I thought I'd post it here so anyone in the future with the same issue doesn't have to feel like as much as a dumbass as I do... ):P

Hope this helps someone ;)

---

