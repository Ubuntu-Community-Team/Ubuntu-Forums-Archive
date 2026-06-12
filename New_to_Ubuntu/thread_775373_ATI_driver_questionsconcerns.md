---
title: "ATI driver questions/concerns"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by JayOB on 2008-04-30
Hi all!

I'm sure a similar situation has been posted before, but I have a question about my drivers...  I have just installed Hardy on a dual-boot system with XP, and everything is going fine; but when I try to install the drivers via the 'restricted drivers manager' option; I get a black screen when I reboot, and I can't even get a terminal to open afterwards.  How do I get my drivers to work?  I can't change my desktop effects at all, and I'm assuming that's why.  I'm very much a 'buntu newbie, so any help would be greatly appreciated...  I have a Radeon X1650 Pro video card, and my xorg file looks like this:  


[PHP]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
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
EndSection
[/PHP]

I really hope that helps!

---

### Post by Thingymebob on 2008-05-12
You should read [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

To me it looks like all you need do is open a terminal and enter
```

sudo aticonfig --initial -f
```

---

### Post by KOTAPAKA on 2008-05-12
Look mate install the driver from ATI the way thay say:
```
sh ./driver.run
```
then go to your xorg file and configure this:
[HTML]Section "Device"
        Identifier  "ATI Mobility Radeon X1400"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Mobility Radeon X1400" ####[IMPORTANT]#### - this must be the same as the name of your card!!!
        Monitor    "Generic Monitor"
        DefaultDepth     24
[/HTML]

Where under Identifier you put YOUR card's name and change the driver to fglrx. then add fglrx to /etc/modules . Reboot and it should be fine. If you've messed everything up I suggest reinstalling Hardy. As a general advice I would suggest giving up Ubuntu and choosing another distro. I think they've gone too far. It never was quite stable but this release is just a deathtrap. And it definitely is not for new users any more! After you've done everything run:
```
fglrxinfo
```
which should give something like:
[HTML]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7415 Release
[/HTML]
then run:
```
fgl_glxgears
```
and check it out. It should run smoothly and you should get about 500 FPS. Hope this helps.

---

### Post by JayOB on 2008-05-19
Yeah...  so I tried 

```
sudo aticonfig --initial -f
```

And the same black screen appears.  I can still access XP just fine, and I can get into Ubuntu via 'recovery mode', but I don't have the faintest idea what to do from there.  Any ideas?

---

### Post by bergqvistjl on 2008-05-19
> **KOTAPAKA said:**
> As a general advice I would suggest giving up Ubuntu and choosing another distro. I think they've gone too far. It never was quite stable but this release is just a deathtrap. And it definitely is not for new users any more! 
I would just like to add that you are completely wrong there, 8.04 is the best version of ubuntu yet, its simple, friendly and quick. and this is coming from a linux n00b. btw to the user having the problem, you could try plugging your monitor into the dvi port of your card, with an adapter if your monitors only vga.

---

### Post by Canis familiaris on 2008-05-19
To get back X:
In the recovery mode

```
dpkg-reconfigure xserver-xorg
```
and select your driver as "vesa"

Then when you can boot into Ubuntu try installing ATi drivers through [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by JayOB on 2008-05-20
Thanks, everyone; I appreciate all the input.  I'm still experiencing issues, though...  I ran 'fix xserver' from the generic mode menu, and that seemed to eliminate the black screen; I installed and ran envy.  Ubuntu still booted to a black screen even after installing the drivers through that program.  So I ran fix xserver again, and I can use Ubuntu, I even get a prompt telling me that 'new restricted drivers are in use' and that the ATI drivers are working.  However, there is nothing that indicates to me that this is so.  I still can't enable desktop effects, nor can I run ATI's Control Center.  Am I missing something?

---

