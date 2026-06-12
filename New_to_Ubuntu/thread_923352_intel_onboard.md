---
title: "intel onboard"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-18
Ubuntu didn't work out. Intel onboard 845 vid card is too old. XP was worse. I went to that page where they list all the things that you might be able to do to fix the resolution on your computer, and did them all. I'm not sure the 915resolution was doing anything, or I wasn't doing it right. But I followed the directions. ([https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto))
It worked when I installed through safe graphics mode, Trying to install through regular mode wouldn't lead anywhere, 20 minutes would go by with just a white box on the screen/ubuntu desktop (yet resolution was normal.) I only have different ram chips. And no better mobo, can't put a vid card in it.
I believe when I had it installed it was at 640 x 480 or something. Does installing through safe graphics mode limit something? I tried the intel website, but then realized after going through their linux drivers page, that ubuntu already had the intel driver installed.
I'm not sure, but I think it started with the vesa, but then after the update it went to intel. With no change in resolution. I edited the xorg.conf file to add a subsection for the monitor values, but that led to a reboot into low-graphics mode. If ram is the problem, I have different types of ram, that won't fit in it.

---

### Post by phidia on 2008-09-18
Is this a desktop or a laptop? If the intel driver that comes with ubuntu is working right then that probably is the best you can do. 

If the computer your asking about is a desktop you may be able to install an aftermarket card.

---

### Post by hellion0 on 2008-09-18
Hold on, I have that chipset!

I don't remember the exact way I fixed my resolution, but I do remember doing so under Kubuntu-desktop, and removing all resolutions from xorg.conf *except* 1280x1024. I also installed in the first place via the Xubuntu Alternate CD.

---

### Post by Elephantman5 on 2008-09-18
> **hellion0 said:**
> Hold on, I have that chipset!

I don't remember the exact way I fixed my resolution, but I do remember doing so under Kubuntu-desktop, and removing all resolutions from xorg.conf *except* 1280x1024. I also installed in the first place via the Xubuntu Alternate CD.
I was thinking about xubuntu. I'm going to go get blanks right now so cool! Yeh, if you can try to remember, post again, I'll be back in about 30 min. 
Desktop.

---

### Post by hellion0 on 2008-09-18
Here's my data from lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

Here's the relevant part of my xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"NEC"
	Modelname	"NEC AccuSync 70"
	Horizsync	31.0-70.0
	Vertrefresh	55.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

Apparently, all the old resolutions came back, but I still have the ability to use 1280x1024 resolution. I also probably have a different monitor than you, so keep that in mind.

What I did was:
1. Installed (X)ubuntu from the alternate CD.
2. Installed kubuntu-desktop and restarted in KDE. (Might want to use the Kubuntu alternate CD to skip this step.)
3. Removed all resolutions from my Monitor section and added in only 1280x1024 in /etc/X11/xorg.conf. Restarted X, logged back into KDE.
4. Used KDE's resolution utility to change to 1400x1050, which changed it to 1280x1024, possibly due to my editing xorg.conf.
5. Restarted in XFCE. The 1280x1024 resolution was kept.

It's haphazard and risky, but it did work for me. I'm sure someone with more knowledge than me can streamline the workaround.

---

### Post by Elephantman5 on 2008-09-18
[quote=

What I did was:
1. Installed (X)ubuntu from the alternate CD.
2. Installed kubuntu-desktop and restarted in KDE. (Might want to use the Kubuntu alternate CD to skip this step.)
3. Removed all resolutions from my Monitor section and added in only 1280x1024 in /etc/X11/xorg.conf. Restarted X, logged back into KDE.
4. Used KDE's resolution utility to change to 1400x1050, which changed it to 1280x1024, possibly due to my editing xorg.conf.
5. Restarted in XFCE. The 1280x1024 resolution was kept.

It's haphazard and risky, but it did work for me. I'm sure someone with more knowledge than me can streamline the workaround.[/quote]

I'm going to try this. I'm thanking you. 
Really appreciate your thorough response.

--
Turns out, weirdly, installing from default disk, in safe graphics mode lends "safe graphics" as standard, and I never could fix it. 
But, installing from the alternate disk (which I figured would do the same thing) actually gives normal graphics. (And this is just from the regular cd.

Should work with Kubuntu, Ubuntu, Xubuntu. Whichever.

So, Alternate cds awesome. :)

---

### Post by Elephantman5 on 2008-09-19
[quote=

It's haphazard and risky, but it did work for me. I'm sure someone with more knowledge than me can streamline the workaround.[/quote]

By the way, I tried out KDE, and I don't really mind the interface. Me likes.

---

