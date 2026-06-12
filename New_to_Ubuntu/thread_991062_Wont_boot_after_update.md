---
title: "Wont boot after update"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Test Pilot on 2008-11-23
Hello I'm new to ubuntu and Linux as far as that goes, i been a long time windows user and decided to try a Linux OS out on my windows PC. I installed ubuntu 8.10 on the same hard drive as windows using duel boot. The installation went every well everything worked without any hangups until i went to update, all i did was click update, all went OK on the update everything worked until i rebooted, now all i get on boot up is a blank brown screen.
I'm thinking that there was some hardware issue with one of the updates, that or i also installed the ati driver that popped up right after installing. I'm not sure where to go from here or if there is a way to get it out of the blank screen? 


I built this computer myself, here are some specs.

ASUSTek Computer Inc. K8N

2.00 gigahertz AMD Athlon 64

NVIDIA nForce3
Board: ASUSTeK Computer INC. 'K8N' Rev 1.xx
BIOS: American Megatrends Inc. 1010.001 12/20/2005

Maxtor 6Y120P0 [Hard drive] (122.94 GB)

Realtek AC'97 Audio
Radeon X1650 Series

Please help!!!

Thanks,
Test Pilot

---

### Post by kansasnoob on 2008-11-23
I'm not real sure what to think here, but I remembered reading this:

> ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information 

From:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

The bug referenced:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

In older versions (7.10 and prior) I'd have recommended this:

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

But as it says:

> UPDATE: This method does not work with Hardy Heron and probably all versions to follow (including Intrepid Ibex). This method seems to ONLY work with Gutsy Gibbon and older.
I think this is because the newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf.

For the most part consider this a <BUMP> from a fellow Kansan:)

---

### Post by Test Pilot on 2008-11-23
Thanks for the quick reply :) Kansas is a good place to live but it gets to cool here for me.

I rebooted in recovery mode and every thing works very well now, other then that i have found no problems at all.
Thanks ubuntu for a great OS \\:D/

---

