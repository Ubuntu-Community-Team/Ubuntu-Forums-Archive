---
title: "Nvidia &gt; ATI?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by etnoo on 2008-09-02
Okay I installed ubuntu 7.10. I'm running an x800 pro ati card. My windows tear when I drag them and videos are a little choppy. This includes streaming videos also. I've heard ATI sucks for linux. Would I be better off just getting an NVidia card?

note: I also tried installing the latest ATI driver, and upgraded to 8.04. Still no luck.

Compiz seems to be the culprit. Seems a little smoother when I turn the desktop appearance to basic but I think its still there.

SO. Nvidia > ATI?

Will I have better luck?

Oh, and I plan on getting dual monitors. Nvidia better in this regard?



Thanks.

---

### Post by brentoboy on 2008-09-02
4 years ago I wold have said "absolutely nvidia>ati"

now, not sure.  I still only buy nvidia, but since ati merged with amd, they have opened up a bit.   Make sure you have the proprietary drivers installed, and, if it is in the way, remove compiz.  It looks cool, but uses a lot of resources, and if performance is a problem, you'll have to let go (or invest)

---

### Post by tuxxy on 2008-09-02
> **etnoo said:**
> Okay I installed ubuntu 7.10. I'm running an x800 pro ati card. My windows tear when I drag them and videos are a little choppy. This includes streaming videos also. I've heard ATI sucks for linux. Would I be better off just getting an NVidia card?

note: I also tried installing the latest ATI driver, and upgraded to 8.04. Still no luck.

Compiz seems to be the culprit. Seems a little smoother when I turn the desktop appearance to basic but I think its still there.

SO. Nvidia > ATI?

Will I have better luck?

Oh, and I plan on getting dual monitors. Nvidia better in this regard?



Thanks.

Your correct, I couldnt recommend nvidia enough - ATI drivers are poor

---

### Post by Vadi on 2008-09-02
Try using Envy ([click]("apt:envyng-gtk"), then go to Applications - System Tools - Envy) to get *the* latest drivers. That might help.

But yes, nvidia > ati atm. Some nvidia cards even perform better than in windows ([click]("http://www.phoronix.com/scan.php?page=article&item=nvidia_workstation_perf&num=2")).

---

### Post by crispy_420 on 2008-09-02
I have an x850, pretty close right?

I have no issues but here is the relevent part of my xorg:

Section "Device"
	Identifier	"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Module"
	Load		"glx"
	Load		"evdev"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640×480"
	EndSubSection
EndSection


Give that a shot. And I do have to admit, ATI/AMD does have some work to do with their drivers. I still get issues of a hard lock on logout when xorg just kills my system. Kind of a pain but what can I do as I tried many fixes that led to no solution. But if you can live with that, don't invest in new hardware yet.

---

