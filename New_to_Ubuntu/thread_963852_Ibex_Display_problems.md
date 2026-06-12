---
title: "Ibex Display problems"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by flusteredpie on 2008-10-30
Hi there,

   Just updated from 8.04 to 8.10 but have run into problems. I can no longer select a resolution > 1024x768 and my only choice of refresh rate is 60Hz. I can also no longer apply desktop effects, whereas I could under 8.04. 

My graphics card is an Intel Corporation Mobile GM965/GL960 (output from lspci | grep VGA). Contents of my xorg.conf are as follows;

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2640 800
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "intel"
EndSection
```

Any suggestions?

Cheers in advance!

---

### Post by LowSky on 2008-10-30
boot into recovery mode and resetup Xorg

IDK if there is a Intel proprietary driver but if there is turn that on too

---

### Post by flusteredpie on 2008-10-30
Just ran dpkg-reconfigure xserver-xorg in recovery mode which I assume is what you were suggesting. It only really seemed to request information about my keyboard, and that was about it. No change to my display options.

The "intel" driver I'm currently using worked fine under 8.04...

---

### Post by flusteredpie on 2008-10-30
Anybody have any other suggestions? Beginning to wish I'd stuck with 8.04!

---

### Post by flusteredpie on 2008-10-30
Right, the problem seems to lie with the new version of xorg. It attempts to autodetect the display and more or less ignores what's in xorg.conf. In my case, it's setting up my display incorrectly. Does anyone know if there's a way to make it stop doing this, and use xorg.conf?

---

