---
title: "Cant get Envy or Nvidia drivers to work"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by mastergunner on 2008-08-31
Guys I have installed Envy and let it run. When it finished downloading the Nvidia drivers and setting them up I have only 2 sizes of screens to choose from. The largest is 640x480. What have I done wrong? Is there a how to on installing and setting up the proper drivers? My card is a Geforce 8500.

---

### Post by gmxgeek on 2008-08-31
please post your /etc/X11/Xorg.conf and /var/log/Xorg.0.log

---

### Post by mastergunner on 2008-08-31
I have uninstalled Envy so I can actually work. I will reinstall and post that. What should those look like if it is installed and properly working?

---

### Post by pfdevil on 2008-08-31
Hello this type of thing is fairly well documented, please follow some of the options here to install the nvidia drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Low%20Screen%20Resolutions]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Low%20Screen%20Resolutions")

---

### Post by mastergunner on 2008-08-31
Here is my xorg config. I have 3 of these though.


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8500 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by gjoellee on 2008-08-31
to fix your resolution: [http://www.kshoster.net/?c=tipsandtricks_xfix](http://www.kshoster.net/?c=tipsandtricks_xfix)

---

### Post by mastergunner on 2008-08-31
I can not post my xorg.0.log cause it says it is too big. What do you need from there?

---

### Post by mastergunner on 2008-08-31
Here is another xorg. It didnt show but ther are x's in fron of the resolutions. I used Kate to see this but cant delete the x's. Whats wrong?


Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8500 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"1400x1050@60"	"800x600@60"	"1600x1200@60"	"800x600@56"	"640x480@60"

---

### Post by mastergunner on 2008-08-31
Guys why is this so difficult? Shouldnt I use envy and have it install everything and it should work fine but all of these issues. Need more help. Appreciate it.

---

### Post by pfdevil on 2008-08-31
Like in my previous post there is extensive written documents about this. Just follow it step by step. Envy is not always fail proof. Just read and you will be able to help yourself.

How do I know this. I followed the guides yesterday.

---

### Post by mastergunner on 2008-08-31
pfdevil I have read the post but I am a noob so I do not understand what I am suppose to do. I need a step by step guide to help me through this. What did you do exactly to get yours fixed?

---

### Post by Gannon8 on 2008-08-31
Since you uninstalled the envy driver, the xorg.conf and xorg.0.log will be incorrect. Reinstall the driver, then post the two files. Try posting them as attachments in the .txt extention.

---

### Post by mastergunner on 2008-08-31
Gannon I have just scewed this thing up. Could you walk me through exactly what I need to do. Thanks.

---

### Post by mastergunner on 2008-09-01
Anyone? I really need help here.

---

### Post by overdrank on 2008-09-01
Hi and I see in your previous post of the xorg that the nv driver was bing used instead of the nvidia driver. If you used Envy to install the drver then it should be the nvidia drvers and you can try and use the nvidia-settings to adjust your resolution. After you install the drivers use the command ```
gksu nvidia-settings 
``` and try to adjust your settings there. If not post back and we will try and assist further

---

