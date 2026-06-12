---
title: "Black screen after splash"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Natsuko640 on 2008-04-28
I recently upgraded my Dell Inspiron 5160 to Hardy Heron; however, after it restarted there would only be a blank screen after the splash unless I had the laptop connected to an outside monitor. I've tried the old dpkg-reconfigure xserver-xorg but it doesn't give me the option to select a driver. When I tried to detect my monitors in the GUI it would only bring up an unknown monitor.

Any idea how I can fix it?

---

### Post by amohanty on 2008-04-29
a. what kind of video card do you have?
b. can you post your xorg.conf?

AM

---

### Post by Natsuko640 on 2008-04-29
The card is a  XGI Volari 32MB.


Here's my xorg.conf



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

---

### Post by amohanty on 2008-04-30
THe volari cards needs the sis drivers, when you get to the gub screen select the recovery mode and then at the prompt do a
sudo apt-get install xserver-xorg-video-sis, in thoery it should be installed by default. Then in your Device section in the xorg.conf file, add the following:
   Driver "sis"

You can edit the file using nano, i.e. at the prompt
nano /etc/X11/xorg.conf

HTH
AM

---

### Post by Natsuko640 on 2008-04-30
When I installed the drivers the prompt said they were up to date, so I wen t on and added the driver to the device. However, the screen still goes blank after the boot process. I took off the splash so after it starts it gives me tty1, but as I try to sign in that way the screen flickers a few times and then just goes black again.

---

### Post by Natsuko640 on 2008-04-30
I figured out my problem. Instead of the sis driver I needed the Trident driver. Thanks for your help, I wouldn't have figured it out without you.

---

