---
title: "Thinkpad t42, radeon 7500 and 8.04 :)"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Gezzy on 2008-05-09
Hi

This linux thing is pretty new to me, so i'd appreciate
some help if I can get some :)

I just did a fresh install of 8.04 on my laptop (thinkpad t42),
and I was wondering about drivers and such.

Everything seems to work out of the box, but...
im pretty sure im supposed to get more performance out of
the radeon. glxgears gives me about ~700 - 730fps while
my friends eeePC gets about ~900fps :)

Anyone who knows where i can find some drivers if they even
exist? If so, give me some instructions on how to install them :)

Any help is very appreciated! :)

ps. forgot the specs, if the matter :P

1.7ghz pentium m
1024mb ram
radeon 7500

---

### Post by Sirron on 2008-05-09
First, check the Restricted Manager. The open source drivers provided by default are pretty good all things considered, but you'll get much better performance from the closed source, proprietary ones.

Alternatively, Envy is a great application that installs the latest ATI or Nvidia driver, you can find out more here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

I believe it's available from the repositories.

---

### Post by guildofghostwriters on 2008-05-09
I'm fairly new myself so this is the blind leading the blind somewhat, especially as I haven't got this to work (although many here have) but...

Are you using the open source drivers or the ATI proprietary drivers? If you're not sure, click on system/administration/hardware drivers and see if ATI accelerated graphics driver is listed and enabled. If it's not, you're probably using the open source drivers and using the ATI proprietary drivers should improve things if you can get them to work. If the ATI accelerated graphics driver is enabled, it may be worth downloading and manually installing the latest ATI drivers - there are many guides and how tos around, try this one - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) 
You can also try using envy (search for envy in synaptic).

As I said at the start, I couldn't get the drivers working for my radeon 9800 pro using any of the methods I found around here and while I'm not alone, there are also many using these forums who've got them working without any trouble so I guess there's just a problem with my configuration at the moment and I'm crossing fingers it's sorted out in time.

Good luck!

---

### Post by Gezzy on 2008-05-09
Thanks for a quick response :)

I tried using Envy, but it gave me an error:

EnvyNG error: Envy does not recognise your card as compatible with any 
version of the driver. This might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

And then the Application crashes :)

A friend told me he thinks the radeon 7500 is Blacklisted or something.
Does that mean i cant get it working ?

---

### Post by Gezzy on 2008-05-09
Hi :)

"system/administration/hardware drivers" shows me two things.

Device Driver
    Atheros Hardware Access Layer (HAL) - in use
    Support for atheros 802.11 wireless LAN cards - in use

Nothing about the graphics card :\

---

### Post by spiderbatdad on 2008-05-09
Hi I have the same card. I believe it is actually a generation behind supported cards for gl rendering...especially aiglx. You need 8000 or better for good performance.

---

### Post by Gezzy on 2008-05-09
here's hoping for a miracle solution then :)
Dont want to go back to windows just because of crappy
performance, not that i am expecting anything special, but maybe a 
little more :)

---

### Post by Gezzy on 2008-05-09
Hey folks, just wanted to let you know i've gotten some headway! :)

After googling for awhile i found that this text, when added
to xorg.conf gave me about ~200 more fps in glxgears. (~900fps instead of
700) Which in turn made Open Arena playable, but still a bit laggy :)

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"LVDSBiosNativeMode" "false"
	Option		"GARTSize" "32"
	Option		"AGPSize" "64"
	Option		"AGPMode" "4"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode" "8"
	Option		"AGPFastWrite" "True"
	Option		"EnablePageFlip" "true"
	Option		"EnableDepthMoves" "true"
	Option		"UseInternalAGPGART" "no"
	Option		"BackingStore" "on"
	Option		"UseInternalAGPGART" "no"
	Option		"DMAForXv" "true"
	Option		"AccelMethod" "XAA"
	Option		"ColorTiling" "on"
	Option		"AccelDFS" "true"
	Option		"TripleBuffer" "true"
	Option		"DynamicClocks" "on"

EndSection

The device section was empty. Any ideas on how to get the fps higher?:)

---

