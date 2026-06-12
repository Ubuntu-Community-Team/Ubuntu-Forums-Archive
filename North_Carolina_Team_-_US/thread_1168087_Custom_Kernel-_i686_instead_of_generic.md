---
title: "Custom Kernel- i686 instead of generic?"
date: 2009-05-23
forum: North Carolina Team - US
---

### Post by mustangzach on 2009-05-23
Okay, I have a Thinkpad 600E running Xubuntu with the following specs:

400MHz Pentium 2
128MB RAM
Integrated graphics
60GB 5,200 RPM Drive, ATA-3 (I think, that or ATA-4)

And an old Gateway running Debian Lenny:

400MHz Pentium 2 Celeron
128MB RAM
ATI Integrated Graphics
60GB, 7,200RPM drive, ATA-3, really old though, so it's really slow.

The Debian Gateway blows the Xubuntu install out of the water! This shouldn't be happening, I mean, the Thinky is clearly a bit faster than the Gateway, and the Debian install uses GNOME, my person favorite GUI.

So, I've determined the issue- the Debian install uses the Linux i686 Kernel, the Xubuntu uses Generic i386. This seems to be the issue to me. I want my install to be more effiecient in every way possible, so I can have that system completely usable. Not only that, but since ever I ran 7.04 on that system, I can't get the audio drivers to work the way I could get the old ones to work. Hopefully by doing this I can get my system running better.

So yeah..

I messed around with custom kernels on FreeBSD a while back, but never with Linux. And that was a long time ago, I haven't used FreeBSD in forever, and forgot how I did it then.


So, how can I compile a custom kernal for my system? Thanks in advance.

---

### Post by snowpine on 2009-05-24
Xubuntu's ram footprint is about double that of Debian Xfce; it has nothing to do with the kernel: [http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

---

### Post by mustangzach on 2009-05-25
Ah yes..

So, is there a way I can make my Xubuntu system more efficent, or will I have to install Debian on that laptop and *really* tweak the interface, as I hate the default XFCE appearence? What's causing Xubuntu to use that much more RAM?


Oh yeah, and why is it the technique used for getting sound to work in the older releases don't work in the newer release? It's kinda bad not having sound when I'm a music addict. 


Thanks for the response.

---

### Post by snowpine on 2009-05-25
Ubuntu/Xubuntu is just too bloated for older hardware, in my opinion. The first version of Ubuntu came out around 2004, and their development efforts just aren't focused on hardware older than that. Debian is an older distro and has greater emphasis on supporting legacy hardware.

I have heard (haven't personally tried it) that a minimal install of Ubuntu, then adding just the base Xfce interface, is lighter/faster than full Xubuntu. [http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

Either way, here's a great resource for tweaking the appearance of Xfce: [http://xfce-look.org/](http://xfce-look.org/)

---

### Post by mustangzach on 2009-05-26
Well, I gave in. I just installed Debian on that Thinkpad, with GNOME though. It ran fairly nice, until I messed up the modules trying to get the wireless card working. So now I'm reinstalling, since it's just as easy lol.. I'll jsut keep Ubuntu on my Acer and on my Dell :)

For some weird reason, I can never get the b43 module to work on any system, even with the firmware cutter. Then I installed the NDIS Wrapper without blacklisting the old drivers (I know- duh moment), and now it's all broke lol. I'm starting over and trying a different technique. Any recommendations?

BTW, on the side note- every computer in my household either runs Debian or Ubuntu. I feel very accomplished. My house is free of Microsoft products. Long live freedom!

---

