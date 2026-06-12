---
title: "X Issues! Virtual Size? (Gutsy)"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by chowanec on 2008-06-29
So -- I just got this sweet television (Samsung LN46A750) and I want to run my linux in widescreen format so that I can view movies, etc. at the right aspect ratio.

I have to run openchrome as VIA makes the better<?> fanless multimedia mini-itx boards... :P

This is taken from my xorg.0.log
```
(II) VIA(0): Not using built-in mode "1920x1080" (width too large for virtual size)
```

Here's the relevant bits from xorg.conf

```

Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection

...

Section "Device"
	Identifier	"Integrated Graphics Chipset"
	Driver		"openchrome"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"VBEModes"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"UseEDID"	"True"
	HorizSync	30-75
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Integrated Graphics Chipset"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1080" "1600x1200" "1360x768" "1280x1024" "1280x768"
	EndSubSection
EndSection

```

Anything obvious that I am missing?  Any help you can provide would be massively appreciated...

Thanks.

-Chow

---

### Post by HalPomeranz on 2008-06-30
Try adding a "Virtual" declaration like so:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Integrated Graphics Chipset"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
               **Virtual         2048 2048**
		Modes		"1920x1080" "1600x1200" "1360x768" "1280x1024" "1280x768"
	EndSubSection
EndSection

```

Depending on your graphics hardware, you may be able to set your virtual display size larger than 2048x2048, but this setting should at least allow you to get to the 1920x1080 display resolution you want.

---

