---
title: "Touchpad speed on ubuntu 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by anarkhy on 2008-10-31
How i can make the touchpad more responsive on 8.10?

here is the xorg but i didnt see the option for mouse or touchpad to edit
[B]
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
EndSection[/B]


and how to install the effects for cube, etc?

---

### Post by talsemgeest on 2008-10-31
In Intrepid, most things are no longer controlled by the xorg.conf, I believe they are controlled by the Hardware Abstraction Layer, but I'm not sure how to control that.

As for controlling the cube, type this in the terminal: ```
sudo apt-get install ccsm
```
Then you should be able to control all of your compiz effects.

---

