---
title: "Intrepid broke my video"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by djen9999 on 2008-10-31
I was under the impression that all I would lose by upgrading to Intrepid was my visual effects and 3D acceleration.  What I lost was everything.  My video card is: C51G [GeForce 6100] (rev a2) and I am currently running on the old Kernel in low graphics mode.  All I get with the new Kernel is a blank screen.  Recovery mode with the new kernel gives me 800 x 600 instead of my 1280 x1084. Low Graphics with the old kernel gives me 1280 X 1084 but funky fonts and the inability to use high resource applications like the Gimp.

This is my xorg file:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Any suggestions?  What else can I try?

---

### Post by Zzl1xndd on 2008-10-31
Depending on how you installed your Video driver you may have to reinstall it for the new Kernel.

---

### Post by ethoxyethaan on 2008-10-31
Hi, use recovery mode to change your Xorg config to default, after you did that boot into the new kernel and look for the new hardware drivers in administration, enable them and restart. this should fix them problem, if not you will need to read this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

and that should solve your problems.
!note: you will have to remove your old video card drivers before you can install a new one.
When you install a new kernel you need to Reconfigure you video card driver. (always)

---

### Post by djen9999 on 2008-10-31
OK, is there someone willing to give me a step by step on how to do that?  I think I have a basic idea but I really don't want to mess this up.

Thanks in advance.

---

### Post by Duck2006 on 2008-10-31
This link gives it to you as to how.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by djen9999 on 2008-10-31
Many thanks, Duck and ethoxyethaan.  I'll see how it goes.

---

### Post by djen9999 on 2008-11-03
It didn't work.  I went through the whole process and I still get the blanc screen.  The installation process even checked the Kernel to make sure everything was OK.  Any other ideas?

---

### Post by djen9999 on 2008-11-03
It didn't work.  I went through the whole process and when I rebooted, the screen was still blank.  The installation process even checked the kernel to make sure everything is OK.  I would continue to use the old kernel but something is causing me to restart periodically.

Any more thoughts?

---

### Post by Duck2006 on 2008-11-03
This one may help.

[http://www.linuxquestions.org/questions/linux-newbie-8/how-i-got-back-my-ubuntu-gui-680600/](http://www.linuxquestions.org/questions/linux-newbie-8/how-i-got-back-my-ubuntu-gui-680600/)

---

### Post by djen9999 on 2008-11-03
Well, that got me my screen back, but I'm at 800 x 600 and it wont change.  I tried activating my restricted driver but that broke the video again.  I tried reconfiguring the xserver but it didn't do anything.

At least I think I'm on the right track.

Any more suggestions?

---

### Post by djen9999 on 2008-11-03
I've been able to get low resolution at 1280x1024 by adding it to xorg.conf in the monitor section, but I can't get my regular resolution and my refresh rate is set at 0.  My hardware drivers settings says that I'm using version 177 which is the recommended driver but I can't get the proper resolution.

---

