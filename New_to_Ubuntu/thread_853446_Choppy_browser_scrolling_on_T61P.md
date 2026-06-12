---
title: "Choppy browser scrolling on T61P"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by vlam21 on 2008-07-08
I've just switched over from Windows and Ubuntu is working very well for me, but I have one minor problem.

I was wondering what piece(s) of hardware is/are related to how choppy/smooth scrolling in a page is, because when I navigate in Firefox, the page moves rather choppily.

I'm on a 2.2 ghz core2duo, 2 gigs ram, 570M nVidia video card (with nVidia drivers installed).

Thank you!

---

### Post by jbrown96 on 2008-07-08
I have the same laptop (2GHz though), and I have never had this problem with Ubuntu. I have had that problem with some of the other distros (OpenSUSE and Fedora). With OpenSUSE it was RAM related. You may want to check that out In a terminal,```
free
``` will give you stats about memory usage. ```
top
``` will tell you about individual processes. 
I'm guessing that it is a driver problem. How confident are you that the nVidia driver is installed? Is Compiz enabled? You can manually check with ```
gedit /etc/X11/xorg.conf
```. I'll attach my file, so you can see, but there is one line in there that describes which video driver is being used. It should say "nvidia". If the driver is not enabled, it will say "vesa". If you need to change it, you will need root privileges. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` This will create a backup file, then to edit: ```
sudo gedit /etc/X11/xorg.conf
```

Btw are you running 32 or 64-bit?

---

### Post by vlam21 on 2008-07-08
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"

I'm not using the default vesa drivers, and I'm on 32-bit Ubuntu.

             total       used       free     shared    buffers     cached
Mem:       2041888     611216    1430672          0      42240     317988
-/+ buffers/cache:     250988    1790900
Swap:      4016208          0    4016208

That's the output of "free" right after I rebooted my laptop. The problem is more easily noticed when I spam up and down on my mousewheel. It takes several seconds after I've stopped spamming for it to process all that I did. When I use Firefox normally (as I don't typically play with the mousewheel like that), it's just choppy. My guess is that there's something up with the drivers.

Thanks for your help. I really appreciate your helping on me with this transition.

---

### Post by sdennie on 2008-07-08
Are you using compiz?  If so, this guide might speed things up: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369).  If not, it's easy enough to remove: Just uncheck it from your startup programs.

---

