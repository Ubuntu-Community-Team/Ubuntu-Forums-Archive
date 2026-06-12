---
title: "My laptop doesn't have a hard drive. Is 14.04 optimized now for flash drive booting?"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by jan59 on 2015-09-05
I haven't tried it yet since I heard Ubuntu takes a lot of read/write rates and will quickly deteriorate a flash drive. So, what would you suggest? Or are there any other Linux distros (except puppy) that would fit my needs?

Thanks in advance!

---

### Post by mc4man on 2015-09-05
I'm not sure 14.04 is 'optimized' for anything but you could run it from a good usb3 flash drive. How well & long it works as an Os drive would depend on quality, speed & type of flash drive.
How well it handles garbage collection is a factor as trim can't be run on usb3 
Here I've tried a SanDisk extreme, it worked OK but I wouldn't use it as an Os drive myself. I know others seem ok with running Ubuntu on a decent thumb drive

I have though run Ubuntu solely on a usb3 ssd for the last couple of years, my latest one, an Adata, has worked well for about a year now. I'd rate it as high midrange external ssd, probably cost around 125 or so.
(- my previous one was a more expensive high end usb3 ssd, it went into the tank after a year or so though the drive either  had some internal breakdown or I screwed it up by doing not 1 but 2 full formats on it for some dumb reason as I think that's a poor idea  on ssd's
 usb3 ssd's also can't use a ATA Secure Erase which would of been what I wanted to do & could possibly fix..

So I'd go with a mid range usb3  ssd if putting a hard drive or ssd internally isn't an option

---

### Post by syscrh on 2015-09-05
I assume it could work fine! But I would enable TRIM support after installing Ubuntu onto the drive: [http://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/](http://www.howtogeek.com/176978/ubuntu-doesnt-trim-ssds-by-default-why-not-and-how-to-enable-it-yourself/)

---

### Post by cdh79 on 2015-09-05
as a test i have installed Ubuntu on a usb2.0 usb-stick and an ssd in an external usb-housing a couple of days ago, and when connected to a usb2.0 interface on a laptop the USB stick was very slow.
the ssd was doing quite well, even when being connected to the very same usb 2.0 port, so i'd definitely recommend choosing an external ssd over a regular usb-stick..

there are actually some usb-sticks with ssd-controllers built in to control the flash (like the corsair gtx .. make sure it's the "B" model, or even the visiontek usb pocket ssd) and they seem to provide very good results.. 
not cheap, but for the size and speed, ok i would say..

edit: here's a video about the visiontek: [https://www.youtube.com/watch?v=P77_UQVk46I](https://www.youtube.com/watch?v=P77_UQVk46I)

---

### Post by grahammechanical on 2015-09-05
Trim is not a function of the Linux distribution but of the Linux kernel. This wiki page was last edited in July this year. So, I suppose we can consider it as up to date information.

[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

Note the point about having Linux kernel 3.2 or newer. That information will make some guides on the web out of date. Ubuntu 15.04 and 14.04.3 have Linux kernel 3.19.

Regards.

---

### Post by syscrh on 2015-09-05
In the case of Ubuntu it's actually a function of this distribution because they activate it by default with several configuration files. But there's one catch: They check if the SSD is in the list of supported devices and any USB eMMC would rather not be in this list. To circumvent this, you have to create your own startup files or disable the checks.

The Debian wiki is actually a bit outdated because discard in /etc/fstab should no longer be used!

---

### Post by mc4man on 2015-09-05
> **syscrh said:**
> In the case of Ubuntu it's actually a function of this distribution because they activate it by default with several configuration files. But there's one catch: They check if the SSD is in the list of supported devices and any USB eMMC would rather not be in this list. To circumvent this, you have to create your own startup files or disable the checks.

The Debian wiki is actually a bit outdated because discard in /etc/fstab should no longer be used!
I'm curious - can you provide some info/link that says trim can work via usb?

---

### Post by syscrh on 2015-09-06
No Ubuntu specific link, but:
- Many Android devices TRIM their eMMC (especially important on the Galaxy Nexus and the Nexus 7 (2012) because of cheap eMMCs) and they're based on Linux
- I found this link (Linux based, too): [http://forum.odroid.com/viewtopic.php?f=65&t=3468](http://forum.odroid.com/viewtopic.php?f=65&t=3468)
- My Raspberry Pis are able to TRIM their MicroSD cards and the connected ext4-formatted USB 64 GB eMMC storage using Minibean (small Raspbian), so I assume doing the same with Ubuntu shouldn't be a problem

---

### Post by HermanAB on 2015-09-06
BTW, don't worry about wearing out a modern SSD.  The embedded controller automatically shuffles things around to level the wear and it will probably outlast both you and the laptop.

---

### Post by syscrh on 2015-09-06
Do you think so?
Personally I've managed to destroy a SanDisk 64 GB SSD within 2.5 years. On the other hand my Samsung 250 GB SSD is still working perfectly fine (ThinkPad X230).

---

