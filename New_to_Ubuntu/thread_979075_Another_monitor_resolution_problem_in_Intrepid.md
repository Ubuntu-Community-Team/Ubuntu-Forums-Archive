---
title: "Another monitor resolution problem in Intrepid"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by fishes on 2008-11-11
Hi,

Many people seem to be having monitor resolutions after installing 8.10; I'm adding to the pile, sorry.  I've looked through a ton of threads and tried many of the solutions, settling on editing my xorg.conf file, but as yet without luck.

I am having a problem getting my monitor's native resolution (1680x1050) to register as an available resolution when the proprietary video driver is enabled.  However, I get the native resolution when the proprietary driver is turned off (but then choppy graphics and no effects). My system: I am running Intrepid on a Dell Optiplex gx270 with a Nvidia GeForce4 MX440 AGP card in it, connected via DVI to a 22 inch Dell Ultrasharp. The Nvidia driver loads correctly through hardware drivers.  Upon restart, however, I become limited to a resolution of 1024x768, and nothing higher is available in Screen Resolution GUI. When stretched over a 22 inch screen this looks exceedingly odd, although effects work.

I've looked through the forums and documentation and am pretty sure this is something I can fix in xorg.conf, but am not sure how exactly to edit the file. I have tried playing around with xrandr, too, but don't know how to specify modelines.

Below are my xorg.conf files before the driver install, after the driver install, and with the "best" edit so far (which get's my resolution up to 1280x1024):

Without the proprietary driver enabled, my xorg.conf read:

```
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
```

My xorg.conf file with the proprietary driver enabled read as follows. I was limited to 1024x768:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

The change that got the best results, although not the correct one was replacing DefaultDepth above with:

	```
SubSection "Display"
        	Depth           24
        	Modes   "1650x1050" "1280x1024" "1024x768" "640x480"
    	EndSubSection
```

Restarting, I now have the option to select 1280x1024, but not 1680x1050.	

Any assistance in getting my monitor's native resolution to show up while the Nvidia card is enabled would be much appreciated.

---

### Post by m_l17 on 2008-11-12
Try this:

[http://ubuntuforums.org/showpost.php?p=6134272&postcount=4]("http://ubuntuforums.org/showpost.php?p=6134272&postcount=4")

or

[http://ubuntuforums.org/showpost.php?p=6071334&postcount=12]("http://ubuntuforums.org/showpost.php?p=6071334&postcount=12")

---

### Post by fishes on 2009-02-04
Thanks!

---

### Post by Walter Melon on 2009-02-04
Did you try selecting restricted and proprietary software in Software Sources?  That worked for my nvidia card when it wouldn't go to a higher res than 800x640. I didn't need to touch the xorg.conf file.

---

### Post by fishes on 2009-02-05
I did try that, thanks.  The problem is that I cannot get my monitor's native resolution (1680x1050) to register as an available resolution when the proprietary video driver is enabled. However, I get the native resolution when the proprietary driver is turned off (with the monitor still connected through the card).  But when that happens, I cannot use Compiz.  This is why I turned to the xorg.conf, in hopes that I could get the native resolution to appear with the proprietary driver enabled.

I basically use the system for DVD playing and as a glorified stereo. Both seem to work well without the driver since I upped the memory reserved for video in the BIOS and noticed some improvement ([http://ubuntuforums.org/showthread.php?t=481558](http://ubuntuforums.org/showthread.php?t=481558)), so I've since made peace with the missing Compiz.

That said, I am still itching to get the system working correctly, just, you know, because.  However, I'm thinking this might be hardware, not software.  Since I first posted, I've learned more about Compiz and video hardware, especially from an install of 8.10 on a MacBook, where I found out about limits to the Compiz supported display size related to video cards, in this case for an extended monitor set up ([http://ubuntuforums.org/showthread.php?t=768761&highlight=compiz+resolution](http://ubuntuforums.org/showthread.php?t=768761&highlight=compiz+resolution)). Since I've gotten everything working on smaller monitors up to 1280x1024 by editing xorg.conf as I noted above, I'm thinking that 1650x1050 might be too much for the video card. It is older hardware, after all.

I would be happy to be proved wrong, but this is all I've been able to figure out.

---

