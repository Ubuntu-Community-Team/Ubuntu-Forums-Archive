---
title: "Ubuntu is running in low-graphics mode"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by 213Wayne on 2011-11-23
Hi
 
I'm getting this error everytime I switch on my laptop:
"Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"
 
When I select either of the options:
Run Ubuntu in low-graphics mode for just one session.
Reconfigure graphics
Exit to console
Restart X
 
It leads me to the console login.
 
How can I solve this problem?

---

### Post by 213Wayne on 2011-11-23
Ubuntu is running in low-graphics mode

---

### Post by lolpenguin on 2011-11-23
What is your graphics card?
Run
```
lspci | grep VGA
```
to find out.

---

### Post by 213Wayne on 2011-11-23
When I type in that command I a whole lot of info.:
This is the graphics card:
VGA compatible controller: nVidia Corperation device 0a29 (rev a2)

---

### Post by 213Wayne on 2011-11-23
That's because i did not use the** grep** command

---

### Post by mastablasta on 2011-11-23
have you tried to install the proprietary Nvidia drivers?

---

### Post by dishbert on 2011-12-07
I've had the same problem since I restored my dual boot XP and 10.04 system after a hard drive replacement.

If I select "restart X" after the warnings everything works fine.

Here are some particulars:

$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

Searching for hardware drivers only finds a software modem driver.

The tail end of the xorg1.log looks like this:

(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:05:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

The xorg.conf file is pretty basic:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I'm sure the answer is obvious in the data above, but not to me!  What do I need to fix?

(This is for my laptop, not the hardware details in my signature block.)

---

### Post by mastablasta on 2011-12-07
it's not the same problem at all as you are using an ATI graphics card. A poorly supported one. You can try updating the opensouirce drivers to latest (experimental) verison.

---

### Post by dishbert on 2011-12-07
Thanks for the reply mastablasta.

I was just trying to avoid starting a new thread with the exact same title.

I don't think the card or driver is the issue because (as stated above):

-  I didn't get the low-graphics message before I restored 10.04 after a hard drive replacement

-  Ubuntu runs fine with regular graphics when I "restart X".

If the issue is the 

"Fatal server error:
no screens found"

how do I modify the xorg.conf to fix it?

dishbert

---

### Post by lolpenguin on 2011-12-08
I don't think Ubuntu uses xorg.conf anymore, try renaming it to xorg.conf.old? I do this instead of deleting so I can easily restore.

---

### Post by ravi sharan on 2012-06-16
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
This is my graphics card. All I get is pink screen. Please help me out.
Moreover, This is what I see when I boot my system :
"The following error was encountered. You may need to update your configuration to solve this problem.
(EE) intel(0): [drm] Failed to open DRM device for 
 pci:0000:00:02.0: No such file or directory.
(EE) intel(0) : Failed to become DRM master
(EE) intel(0) : No valid modes
(EE) Screen(s) found, but none have a usable configuration."

---

