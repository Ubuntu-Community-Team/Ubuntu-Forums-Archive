---
title: "External monitor"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Durthor on 2008-06-17
Hi, yesterday i installed ubuntu (for the first time) on my laptop, a Compaq Evo N1020v. But when i turn on my computer it works fine untill after the ubuntu loading screen. then my external monitor says "no signal". it's an Acer AL1916W if that helps... and also ubuntu keeps freezing like every 30 mins..

Thanks for any help! :)

---

### Post by Durthor on 2008-06-17
anyone? please? :(

---

### Post by Durthor on 2008-06-18
oh well... i'll just have to go back to crappy xp... :-x:sad:

---

### Post by kesman on 2008-06-18
Did you try the built-in resolution and monitor configuration tool after you logged in? It's under system -> preferences -> screen resolution.

---

### Post by Durthor on 2008-06-23
yup... didn't work...

---

### Post by GepettoBR on 2008-06-24
I have the same laptop, and I'm sorry to say the linux ATI drivers just can't handle dual monitors with the Radeon IGP 340M. I dual-boot Windows for the sole purpose of watching videos on TV-Out.

---

### Post by Mr.Sonic on 2008-06-30
Aw no.

This was the last hurdle before I wiped Xp of my laptop for good.

Everything else went so good.Knew ubuntu was too good to be true.

:(

---

### Post by thschiavo on 2008-07-01
> **GepettoBR said:**
> I have the same laptop, and I'm sorry to say the linux ATI drivers just can't handle dual monitors with the Radeon IGP 340M. I dual-boot Windows for the sole purpose of watching videos on TV-Out.

Oh really? I have Acer Aspire and I`m experiencing the same problems, with GMA 3100 (intel) as graphic card. :(

---

### Post by GepettoBR on 2008-07-01
> **thschiavo said:**
> Oh really? I have Acer Aspire and I`m experiencing the same problems, with GMA 3100 (intel) as graphic card. :(

That's funny, Intel graphics cards are the best in terms of Linux support. Are you sure you have the latest drivers and that your monitor incorrectly detected by X?

---

### Post by thschiavo on 2008-07-02
> **GepettoBR said:**
> That's funny, Intel graphics cards are the best in terms of Linux support. Are you sure you have the latest drivers and that your monitor incorrectly detected by X?

Are you serious? Everyone says that Intel`s Graphics Cards are the worst ones. I can configure all the compiz effects and everything in 7.10. But the drivers seems to be like... "generics", something like xserver-xorg-video-intel+"Intel - Experimental (...)".

Conclusion. In 7.10, I had to configure all these drivers. In 8.04, I had to do nothing. And in 7.10, I could use two monitors. In 8.04, it crashes. Any idea?

---

### Post by GepettoBR on 2008-07-02
Well, Intel dislcoses all the documentation, so the drivers should be easier to deal with. If you're using the generic driver, that might be the proble.

What's the model of your graphics card? If you don't know, type lspci in a terminal and post the output here.

A propósito, acabei de perceber que você também é brasileiro. Bacana encontrar um colega brazuca num fórum internacional. :)

---

### Post by thschiavo on 2008-07-06
My graphic card? Intel GMA (Graphics Mobile Accelerator) X3100, do you need any additional information? If it's the case, I put here lspci.

> **GepettoBR said:**
> 
(...)A propósito, acabei de perceber que você também é brasileiro. Bacana encontrar um colega brazuca num fórum internacional. :)
Hahaha, legal mesmo! É bem difícil achar brasileiros aqui.

---

### Post by GepettoBR on 2008-07-06
Do you have the "xserver-xorg-video-intel" package installed? The latest intel drivers are supposed to be in the repositories.

If you don't have it, make sure that the extra repositories are enabled in System>Administration>Software Sources and type ```
sudo apt-get install xserver-xorg-video-intel
``` in a terminal, or find the package in Synaptic.

The only thing I can think of if that doesn't work is something wrong with your xorg.conf, so if it doesn't work post its contents here and we'll continue troubleshooting :)

---

### Post by thschiavo on 2008-07-08
Since you're from Brasil, see this, please.

[http://jhonlennon.spaces.live.com/blog/cns!1A24BD5E4B799269!224.entry](http://jhonlennon.spaces.live.com/blog/cns!1A24BD5E4B799269!224.entry)

I wrote this because some of my friends just can't install the right drivers.

---

### Post by GepettoBR on 2008-07-09
Weird, if you have the right driver installed it should work.

Did you take a look at your xorg.conf file? When I couldn't enable desktop effects, what finally solved it for me was tweaking that file. For some reason, it didn't specify the driver for my video adapter (weird, since the man page says that field is obligatory) and adding a line to the device section reading [Driver   "ati"] fixed it. Maybe you have a similar situation.

---

### Post by thschiavo on 2008-07-09
When I was trying to activate my desktop effects, I actually tried to modify my xorg.conf and other files, but I was never able to activate the effects. I could not find anyone else in internet who did it, so I wrote that article, specially becaue some of my friend was trying it too.

If you want, I can put my xorg.conf here. Would it help? (I'm not in Ubuntu right now, I'm trying FreeBSD :guitar:)

---

### Post by GepettoBR on 2008-07-09
Please do, and I'll see if I can help figure this out.

and how're you liking BSD? I was thinking of trying it myself.

---

### Post by thschiavo on 2008-07-11
FreeBSD? It's really stable... for example, I'm using apache with the BSD and all looks fine until now. Probably, I'll use it in my server computer.

About xorg.conf, here it is:

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

---

