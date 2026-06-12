---
title: "[SOLVED] fglrx screen resolutions! stuck at 640 480"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by sdowney717 on 2008-10-09
I dont have any screen resolutions beyond 640 by 480
driver is apparently working. installed by envy
any help would be nice to fix this.


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	640	480
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by sdowney717 on 2008-10-09
I needed to run
aticonfig --initial

now it is working
does ENVY not do this?

---

### Post by sdowney717 on 2008-10-09
ok, it is using mesa not fglrx for 3d

---

### Post by porchrat on 2008-10-09
please copy and paste the ouput of this command for us:

```
fglrxinfo
```

P.S.  Is this thread solved or not?...if not please turn off the "SOLVED" label (you do this by going to "thread tools" in the top right corner and selecting "mark thread as unsolved"...or something like that...if you don't you may get fewer responses as people think it has already been dealt with.

---

### Post by sdowney717 on 2008-10-09
scott@scott-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

scott@scott-desktop:~$

I tried using the hardware manager drivers in system admin. It removed envy-fglrx and I nstalled the ubuntu supported FGLRX drivers.
still no 3d

---

### Post by porchrat on 2008-10-09
What graphics card are you using?

---

### Post by sdowney717 on 2008-10-09
an ATI 9600 

It used to work with compiz and 3d on another ubuntu computer, and is supported by ATI driver.

this link was no help
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

---

### Post by porchrat on 2008-10-10
This guide explains how to remove the MESA drivers from your system.  You should really consider just installing the drivers manually as it results in a better install:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

If that is too much reading for you then basically just try this and see if it works:

```
sudo apt-get remove xserver-xgl

```

You should be able to restart and run an "fglrxinfo" to see if mesa is still running in place of fglrx.

otherwise I would recommend you start from the beginning by running:

```
sudo apt-get remove xorg-driver-fglrx
```

then change your /etc/X11/xorg.conf where it says "fglrx" change it to "ati" to ensure that your x-server will start again.  Then do the manual install from this guide...which I will post a link for again...because it is awesome.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by sdowney717 on 2008-10-16
xgl is not installed on that computer.
what about the intel 82875 issue with agp detection? Is it a myth or a real problem. that board uses 82875 with an agp card.

I went thru a lot of misery sifting esoteric web postings about blacklisting edac modules but never got anywhere.

---

### Post by seatownflyer on 2008-10-16
I had problems with this as well.  mine started with my pc going straight to a black screen and locking up.  once I got back in with the recovery console, fglrxinfo said i was running the mesa drivers.  I found a post in these forums saying to change the agp aperature/texture size in the bios.  I tried that and it worked!  I changed mine from 128 to 512.  just fiddle with that i guess.

---

### Post by sdowney717 on 2008-10-16
I tried running it up from 64 to 128.
no difference.

---

