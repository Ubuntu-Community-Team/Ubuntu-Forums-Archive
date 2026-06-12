---
title: "Distro with Broadcom support?"
date: 2008-06-04
forum: Other OS Talk
---

### Post by mivo on 2008-06-04
I managed to get a not too shabby laptop (2 Ghz, 512 MB, 30 GB) for free and plan to use it for some basic stuff. Ubuntu and Fedora didn't like the Broadcom wireless adapter and gOS also had issues with the video system. Before I frustrate myself with ndswrapper, are there any distros that work out of the box with that type of wireless device? (Should ideally have a LiveCD.) Right now the laptop runs with XP, which works for my purpose, but eh, I haven't used any Windows in quite some time, so I'd prefer some flavour of Linux. I'd just like to keep the fiddling to a minimum.

---

### Post by aysiu on 2008-06-04
I doubt it. The whole reason that Broadcom doesn't work is its lack of opening up or porting its drivers to Linux. If one Linux distro could reverse engineer the driver, all the Linux distros would have that. If the driver was built into the Linux kernel, all the distros would have that.

---

### Post by MONODA on 2008-06-04
i remember hearing that opensolaris does, but I might be wrong.

---

### Post by adityakavoor on 2008-06-04
Linux Mint Elyssa .. but I am not sure

---

### Post by mivo on 2008-06-04
Thanks guys. I'll torrent the Mint RC2 and give it a whirl. Solaris is "too different", but I'm curious, so I'll check this out as well. Will report back on both. If all fails (and aysiu made a good point), I might just keep XP on it for a while until I get in one of my tinkering moods. :) I'll basically only play Go (board game) on it, plus some web surfing in the garden, so my needs are easy to meet (Java, firefox).

---

### Post by ch_123 on 2008-06-04
Im pretty sure one of my friend's Ubuntu PCs has a Broadcom adaptor, using restricted drivers. Then again, maybe they only have drivers for certain chipsets.

---

### Post by ptempel on 2008-06-04
Try the correct windows driver with NDIS wrapper.  I was able to get my laptop (HP Pavilion dv6830) wifi working with Ubuntu 8.04 this way.  I used the Broadcom driver from Dell.  This web page helped me out:

[http://goinglinux.com/articles/BroadcomNDIS.html](http://goinglinux.com/articles/BroadcomNDIS.html)

Maybe it can help you?

---

### Post by init1 on 2008-06-04
> **mivo said:**
> I managed to get a not too shabby laptop (2 Ghz, 512 MB, 30 GB) for free and plan to use it for some basic stuff. Ubuntu and Fedora didn't like the Broadcom wireless adapter and gOS also had issues with the video system. Before I frustrate myself with ndswrapper, are there any distros that work out of the box with that type of wireless device? (Should ideally have a LiveCD.) Right now the laptop runs with XP, which works for my purpose, but eh, I haven't used any Windows in quite some time, so I'd prefer some flavour of Linux. I'd just like to keep the fiddling to a minimum.
I have a Broadcom, and Hardy is the first distro to recognize the card without ndiswrapper. If hardy doesn't work, I'd try Mepis. It works for my card.

---

### Post by jrusso2 on 2008-06-04
I have heard PCLinux has it and I think Mandriva does too. 
Ubuntu's Free Software only philosophy keeps it in the repos since its at least partly proprietary.

I think they are working on finishing drivers and firmware for most of the common wireless cards so they will all be open source soon so these problems might be a thing of the past hopefully.

---

### Post by AdamWill on 2008-06-05
The native Broadcom drivers themselves (bcm43xx, b43legacy, b43) are not proprietary, they're fully open source. The issue is that like many drivers, they require firmware, which is not open source. For most drivers, the firmware can at least be legally redistributed by distribution vendors, but for Broadcom, this is not the case. The firmware is not available separately from the Windows driver, and the license terms on the Windows driver do not permit third-party redistribution.

So you'll find that no distro which has an actual company behind it - Ubuntu, Mandriva etc - includes the Broadcom firmware. A few, which are made by individual enthusiasts or small communities, do include it, but this is technically a breach of Broadcom's license on the firmware.

To actually use the native drivers, you have to extract the required firmware from a copy of a Windows driver, using the bcm43xx-fwcutter or b43-fwcutter tool (depending on which driver you're trying to use). For bcm43xx, you need a version 3.x copy of the Windows driver. For b43 and b43legacy, you need a version 4.x copy of the Windows driver. The best place to look to find a good copy of the driver is [http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation) .

Mandriva's GUI network configuration tool automates this: when you try to use bcm43xx in Mandriva, it asks for a copy of the Windows driver, and runs bcm43xx-fwcutter on it for you, so you don't have to do it manually. I don't know if Ubuntu does anything like this.

Practically speaking, I frankly usually recommend using ndiswrapper anyway. In my experience (personal experience with my own laptop, and reported experience of several others), ndiswrapper is more reliable than the native drivers on most Broadcom chips, at present.

---

### Post by Novega on 2008-06-05
> **AdamWill said:**
> 
Mandriva's GUI network configuration tool automates this: when you try to use bcm43xx in Mandriva, it asks for a copy of the Windows driver, and runs bcm43xx-fwcutter on it for you, so you don't have to do it manually. I don't know if Ubuntu does anything like this.

That would be a great suggestion for Intrepid. Broadcom problems seem fairly prominent within these forums and I personally know of two people who refuse to run Ubuntu (or any distro) because of the poor hardware support (specifically the bcm43xx)

I'm fairly new around here myself, but I tried to install that card for them (by following the guides available online) and was unsuccessful all but once. Some distros don't even see the card when I type -lspci   (*buntu usually shows it) so I din't bother even installing the firmware on those ones b\c the OS doesn't even show the port as populated. In a situation like that how is someone even supposed to know which driver to use? bcm43? bcm43legacy? bcm43xxx? 

Even if the distro *does* recognize that the card is connected to the MB, another factor is the way fwcutter depends on kernel version (ie: if your kernel is ___, then use broadcom driver version ___,   if your kernel is newer than ___ but older than ____, use broadcom driver ___. )  This gets frustrating :mad:

Before anyone ignites their flame machine or claims this isn't the fault of the distro but rather the hardware maker, Please understand that these are issues that affect the usability of the software and are factors that people consider when deciding to make the switch from Windows. I'm not trying to criticize but rather explaining the problems I've experienced or seen others experience firsthand.

---

### Post by mivo on 2008-06-06
Thanks for the additional information and suggestions. Very insightful! :)

I tried Mint (Elyssa RC2), and it had the same issue as Ubuntu. I'll say though that it looks very sexy and is very polished. This is really what Ubuntu needs to look like out of the box. :) They did a great design job. On a side note, none of the distros I have tried yet had any advanced configuration options (graphical) for the touchpad. In XP, I can change the sensitivity, the "tap speed" (to prevent accidental misclicks, etc.), which is another thing on my "must have" list for this laptop (I have a heck of a time with the touchpad).

Ironic side note: XP locks up on me for 5 minutes at a time about twice a day on this laptop. Nice reminder of just why I use Linux on my other two computers. ;)

---

### Post by AdamWill on 2008-06-06
novega: the three native drivers are all part of the same development effort.

originally, there was just bcm43xx .

Then a change happened in the upstream kernel. There's an underlying kernel layer on which development of most wireless drivers is based. This layer was changed. The old one was 'softmac'; the new one is 'mac80211'. So most kernel wireless drivers are being ported from softmac to mac80211.

b43 was the port of bcm43xx to mac80211. This took quite a long time, and the two branches were both actively developed for a while, and acquired some differences beyond just softmac vs mac80211. Some changes were made in b43 to improve the support for newer devices and add new features, but these had a negative effect on support for older devices (bcm4303, bcm4306 revs 1 and 2). So a new branch of the driver was created: b43legacy , which is a mac80211-based driver but designed to work with these older chips.

So that's why there's three drivers. bcm43xx is now deprecated and no longer developed, and will probably disappear quite fast in future.

The version of the Windows driver you need does not technically depend on the kernel version but on whether you're using b43/b43legacy, or bcm43xx - as I wrote in my first post. You need v3.xx for bcm43xx, and v4.xx for b43/b43legacy . The reason this is sometimes phrased in terms of kernel version is because the upstream kernel switched from including bcm43xx to including b43; I believe at version 2.6.24, though I could be wrong there. However, this won't always hold true for all distros; for instance, we (Mandriva) patched the 2.6.24 kernel included in 2008 Spring to use bcm43xx rather than b43/b43legacy, because in our testing, bcm43xx still worked better. We'll probably drop bcm43xx and go for b43/b43legacy for 2009, though.

In future the situation will be pretty clear: the correct driver for the card will be automatically loaded. The kernel 'knows' when to use b43 and when to use b43legacy (via modaliases). It's only still confusing while many distros and users are still sticking to bcm43xx.

If a distro doesn't see the card at all - it doesn't show up on lspci output - then it will never work, no matter what driver you load. There's some more fundamental problem in that distro that you'd have to fix first.

---

### Post by mivo on 2008-06-08
Just an update:

I tried a number of different distros and in the end decided to install Xubuntu 8.04 today since with only 512 MB RAM I wanted something relatively light, but still complete out of the box (tried Ubuntu, Fedora, Mint, Zenwalk, gOS, and Xubuntu). Xubuntu was the only distro that I tried that had an adequate graphical tool to change the sensitivity and double-click-speed for the touchpad (in Ubuntu and Mint the settings were ignored).

As for wireless, I went with the easiest method I could find: the "native" driver. I only needed to add the repository from [here]("http://ubuntu.cafuego.net/dists/hardy-cafuego/"), install the bm43-firmware package, reboot, and the wireless connection was automatically picked up. This was much less painful than I had expected.

And I'm glad all my machines are once more Linux-only. Just feels more "at home". I never had a problem with XP on other machines in the past, but on the laptop it was slow and sluggish, and it froze twice a day for stretches of five minutes (usually after hibernating). 

What doesn't work is hibernating. The laptop comes back, but the screen stays black, but I recall seeing threads about this, so it's either known or fixable, or both.

---

### Post by Midwest-Linux on 2008-06-09
I have nothing to add except I will be watching this thread closely. I have a HP FT762NR laptop with Vista and Hardy. Hardy works great except for the built in wireless (Broadcom Hell). Yes I have tried all the suggested scripts at the terminal. One thread/post even said some kind of blue light would come on when everything is configured. 

Another says do the scripts and restart and I still try to access the wireless up where the network icons are (Configure Wireless)...and no other networks show up...I try to type my ID and when I try to type anything into the BSSD I get a beep from the keyboard. Yes I even tried a add on wireless USB adapter and found a Linux driver for that and no go. 

I am clearly missing something here and just not getting it. Surely if the broadcom is not working, a separate outboard USB wireless would world (Trendnet 424UB)...and found a Linux driver at sourceforge. Well that didn't work either...which means I am missing some kind of "view available networks window" separate from the one available from that network icon.

 Is there some kind of different "view wireless networks" window that is supposed to work instead of the network icon where you click configure wireless and that brings up a separate window?

 Is there a pictorial or step by step photo gallery that would visually explain this better? 

 I would love to dump the Vista portion entirely and go with either Ubuntu or Linux Mint 5.0. exclusively. But Vista is only where I can access the wireless for now. I didn't expect a answer  here, but I am willing to bet others are facing the same issues too...despite the excellent threads on having wireless on Hardy.

 I'll keep checking back here and see where I missed something and try yet again. Thanks for your comments.

---

