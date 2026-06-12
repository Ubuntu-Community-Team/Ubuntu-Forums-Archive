---
title: "Pls Help: Lost Gnome Display"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-06-24
I urgently need your help.  Dual-boot XP-Ubuntu 8.04.  This evening I upgraded from 2.6.24-17 to 2.6.24-19 as prompted in the task bar.  After restarting the system, all I see is a black screen with commands in white.  One of the lines states: "not starting GNOME display manager because it is not the default display manager".  I did try using the recovery mode in Grub menu but failed to get the graphical user interface of Gnome back, i.e. the way it was before.

Thanks a lot for your help.  I am forever grateful.

---

### Post by iaculallad on 2008-06-24
> **iClouseau88 said:**
> I urgently need your help.  Dual-boot XP-Ubuntu 8.04.  This evening I upgraded from 2.6.24-17 to 2.6.24-19 as prompted in the task bar.  After restarting the system, all I see is a black screen with commands in white.  One of the lines states: "not starting GNOME display manager because it is not the default display manager".  I did try using the recovery mode in Grub menu but failed to get the graphical user interface of Gnome back, i.e. the way it was before.

Thanks a lot for your help.  I am forever grateful.

Using your recovery mode "terminal":

```
sudo dpkg-reconfigure gdm
```

---

### Post by iClouseau88 on 2008-06-25
Hi, 

Thanks for your prompt reply.  Could you please clarify "recovery mode "terminal""?  I don't recall seeing "terminal" in one of the Grub menu items.

PS:  I clicked on the last icon, i.e Quick Reply  icon to reply but it doesn't work.  I had to use the "normal" reply button.  Please help!

---

### Post by winfree on 2008-06-25
It seems that you end up in a terminal session. If you are not sure, type "whoami' you should see your id on the screen, if not login, then type the command from the prior message:
sudo dpkg-reconfigure gdm

---

### Post by iClouseau88 on 2008-06-25
OK, I got Gnome display back, BUT it is only 80% of the original screen, because now it is on top of a larger black screen which fills the laptop screen.  How do I fix this, and how do I post quick reply,since the 3rd icon in the bottom of each post doesn't do anything.

Edit: carriage return icon, not 3rd, for Quick Reply.

By the way, I thank all who replied with helpful suggestions and I would very much appreciate any help with activating Quick Reply, since this latter problem is driving me up the wall.  I did allow scripts in the options button of Firefox' No Script extension, still no go!

---

### Post by iaculallad on 2008-06-25
Try to execute:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure your xorg file. Try answering the questions with the best of your knowledge (use default values if required).

---

### Post by forger on 2008-06-25
what graphics card do you have?

---

### Post by iClouseau88 on 2008-06-25
My graphic card is Trident Microsystem's CyberBlade XP (Intel 82815 AGP chipset).  It's built-in for Toshiba Satellite Pro 4600 laptop.

By the way, I just discovered that I have to allow yahooapis.com (91.189.94.12) so that the carriage return icon can be used to activate quick reply.  I have always thought that I would just need to allow "ubuntuforums.com".

One solved, but how do I make GDM fill my laptop screen?

Thanks to all, in advance!

---

### Post by iClouseau88 on 2008-06-25
Here's the printout of myxorg.conf file:


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
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

It's strange that there are no video-card specific data such as Horizontal & Vertical refresh rates, video chipset, etc.  I am using a Toshiba Satellite Pro 4600 with onboard Trident Microsystem's CyberBlade XP (Intel 82815 AGP chipset). I suspect that the video driver was wiped out by updating to 2.6.4.19 kernel.

Can someone show me how to get my GDM backto normal, i.e. filling the entire laptop screen as before?  Thanks in advance.

---

