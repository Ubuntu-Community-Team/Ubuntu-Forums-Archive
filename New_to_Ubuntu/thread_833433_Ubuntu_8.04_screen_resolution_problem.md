---
title: "Ubuntu 8.04 screen resolution problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Esoj on 2008-06-18
Ok, first of all, this is my first time using ubuntu. Now i installed it just fine, but since im using two machines (one with ubuntu and one with windows) I had to use a KVM cable to switch between a set of keyboard/mouse for both machines. 

Before I used this cable, my maximum screen resolution was 1680x1050, now after i connected the KVM cable the max screen resolution i get is 1280x800 on ubuntu while on windows i get the whole 1680x1050 resolution.

Ive been searching online hoping i found an answer to this problem but no luck so far. Any help will b appreciated.

Thanks.

---

### Post by philk949 on 2008-06-18
Hi esoj,
Forgive me for posting without a solution, but I just wanted to let you know I'm having the same problem i.e. Hardy 8.04 with Windows XP connected via KVM switch. The difference is, I'm unable to get out of 800x600 and it's making my computing experience a total pain. I'll be very interested to see what solutions are offered. When I posted, the reply below is what I received. Hope you do better.

"please post your /etc/X11/xorg.conf"
 
philk

---

### Post by Esoj on 2008-06-19
> **philk949 said:**
> Hi esoj,
Forgive me for posting without a solution, but I just wanted to let you know I'm having the same problem i.e. Hardy 8.04 with Windows XP connected via KVM switch. The difference is, I'm unable to get out of 800x600 and it's making my computing experience a total pain. I'll be very interested to see what solutions are offered. When I posted, the reply below is what I received. Hope you do better.

"please post your /etc/X11/xorg.conf"
 
philk

don't worry about it mate.

This is pretty lame, I still don't know what to do.

Anyway here is my xorg.conf


> Section "InputDevice"
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
	Option		"UseFBDev"		"true"
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
EndSection

---

### Post by dross_kuh on 2008-06-19
make sure you have the restricted drivers installed.
gksudo nvidia-settings  ## in a terminal
if that does`nt work use aptitude to install nvidia-settings...
once you have it running change the resolution for your monitor from auto to 1680x1050 or whatever u want ...  save and re-login or reboot
hope that help`s

---

### Post by Esoj on 2008-06-23
> **dross_kuh said:**
> make sure you have the restricted drivers installed.
gksudo nvidia-settings  ## in a terminal
if that does`nt work use aptitude to install nvidia-settings...
once you have it running change the resolution for your monitor from auto to 1680x1050 or whatever u want ...  save and re-login or reboot
hope that help`s
well that didnt work for me, it seems it crashed my desktop display and the resolution it gave didn't match with the monitors's so I could only boot the system in prompt mode

---

