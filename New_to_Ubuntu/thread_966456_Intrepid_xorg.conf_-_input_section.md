---
title: "Intrepid xorg.conf - input section"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-11-01
Just had a look at my xorg.conf file after upgrade to intrepid, and there is no input setion anymore.

Has this been moved to a new file or is my .conf file incomplete.
this is all it contains :-


[HTML]Section "Device"
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
EndSection[/HTML]

---

### Post by Kevbert on 2008-11-01
Good one. My xorg.conf is the same, so it's complete.  I too would like to know where the keyboard and mouse settings are kept now.

---

### Post by Sealbhach on 2008-11-01
Saw this in the release notes:

> X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)



.

---

### Post by celticbhoy on 2008-11-01
Yeah its a bit of a problem as I want to set up a graphics tablet.

---

### Post by celticbhoy on 2008-11-01
A lot of how-to's are now out of date then!!!!

---

### Post by philinux on 2008-11-01
> **celticbhoy said:**
> A lot of how-to's are now out of date then!!!!

Only if you're using Intrepid. :)

Xorg is set to disappear completey.

---

### Post by Sealbhach on 2008-11-01
> **philinux said:**
> Only if you're using Intrepid. :)

Xorg is set to disappear completey.

Judging by the number of Xorg related problems on this forum, I think that may be a good thing.


.

---

### Post by celticbhoy on 2008-11-01
That depends on what it is replaced by. I do think there will be a bit of confusion though especially for new users on intrepid looking at old posts from searches.

---

### Post by phidia on 2008-11-01
Actually xorg has been changed since hardy. Now hal is "in charge" of input devices.
See the link [here]("https://wiki.ubuntu.com/X"). Specifically look at the "Using X in Ubuntu" section and the "X/InputHotplug" subsection.

---

### Post by celticbhoy on 2008-11-01
The release notes dont state where the mouse config is, and by association where a graphic tablet config file would be.

---

### Post by phidia on 2008-11-01
> **celticbhoy said:**
> The release notes dont state where the mouse config is, and by association where a graphic tablet config file would be.

Release notes are not documentation-see my previous post here. 
Input devices are handled by HAL.

---

### Post by celticbhoy on 2008-11-01
Yeah I was typing when you posted so last post is redundant.

---

