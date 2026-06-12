---
title: "display configuration help."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Zacariaz on 2008-06-23
Hi, I am the (un)happy owner of a Toshiba Satellite Pro A100 (psaace) featuring:

Display:
size : 15.4 "
type :Toshiba TruBrite® WXGA TFT display
internal resolution : 1,280 x 800
(sync rates seemingly unavailable)
Graphics Controller:
manufacturer : ATI
type : Mobility&#8482; Radeon® X1600 with HyperMemory&#8482;
memory : 128 MB + up to 384 MB
memory type : DDR Video RAM + DDR2 RAM (system memory)
connected bus : 16x PCI Express

I'm currently running a resolution of 1280*768 on my laptop display, while I am able to live with this, I would very much like to get corrected.

I am now also the proud owner of a Samsung LE37S86BDX 37" LCD TV which I would very much like to connect to my laptop.

Now, I have been trying to fix these issues for more than a month now. I know that there is a lot of posts regarding this subject already, but that is actually part of the problem as it is hard to the help you need.

I have failed in my effort, which bothers me a lot, and though I don't expect you to solve my problem just by snapping your fingers, I would very much appreciate any help you could give.

xorg.conf: (irrelevant info removed)
```
...

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

...

Section "Module"
	Load		"glx"
EndSection
```

(personally I don't think this looks quite right.)


Thanks

edit:
I am using the proprietary ATI drivers
edit2:
found some specs for my tv:
D-Sub Input:
VESA
resolution: 1360*768
H Freq: 47.712 kHz
V Freq: 60.015 Hz
Pixel Clock Freq: 85.800 MHz
Sync Polarity (H/V): +/+

I also have info for lower resolutions in case this is too high.

---

### Post by tinny on 2008-06-23
I have an ATI graphics card that I have successfully configured to work with the fglrx driver and S-Video out. Here is my xorg.conf.

```

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "EnableMonitor" "tv"
	Option	    "TVFormat" "PAL-B"
	Option	    "TVStandard" "VIDEO"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "clone"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

Alternatively you can also use aticonfig to set this up (probably best to let aticonfig do this for you).

```

sudo aticonfig --overlay-on=0 --enable-monitor=tv --tv-format-type=PAL-B --tv-standard-type=VIDEO --overlay-type=Xv --desktop-setup=clone

```

Hope this helps.

---

