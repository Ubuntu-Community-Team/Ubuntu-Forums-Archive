---
title: "Which driver should I use for Radeon R9 270X in 12.04?"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by mullet_death on 2014-05-21
I have had some pretty bad experiences gaming on this card in Ubuntu. The card works fine with the supplied drivers from the CD in Windows, for my Linux Steam games like Left 4 Dead 2 or the Hal-Life franchise, I get atrocious performance in-game, especially at the start of a level, even playing at my TV's native resolution. Worse than general bad performance- i.e., awful frame rate and stuttering or whatever it is that it's doing, is the outright freezes, which force me to hard reset my box. Steam gives a dialog every time I log in saying something about using an older version of the fglrx driver, and it recommends the use of fglrx-experimental-13. If anything, fglrx-experimental-13 just makes the crashes occur more frequently. I have tried all three proprietary drivers listed in the “Additional Drivers” menu, and I've had largely the same results. Obviously, not using a driver isn't an option either, especially since I don't even have HDMI aduio output without one, not to mention games being totally unplayable.  

 

 Basically, what driver should I be using? Have I missed something? Is there an alternative to these fglrx drivers? I can provide any more info about my system if necessary.

As a secondary question, if I were to upgrade to Ubuntu 14.04, would the situation change any-- like, is there a better driver for that version of the os or something? 

 

 If I had known ATI cards apparently have so many issues with Linux then I probably would have purchased a different graphics card. :(

---

### Post by bcschmerker on 2014-05-22
As I understand things, the [Free Desktop Organization](http://www.freedesktop.org/) is right in the middle of developing drivers for the brand-new Advanced Micro Devices® Radeon® R5/R7/R9 series of PCIe x16 cards.  The same manufacturer's Radeon® HD™ 6850, 6870, 6950, 6970, 7850, 7870, 7950, and 7970 are already supported in the X.org Radeon driver (package: **xserver-xorg-video-radeon**) and probably would have been a better fit to your situation.

---

### Post by mullet_death on 2014-05-22
Forgive me, I'm new to Linux, certainly to the CLI. I tried installing that package with sudo apt-get install xserver-xorg-video-radeon. I got some error message about unmet required dependencies, so I just went ahead and installed those first. I then tried the original command again and get output basically saying that package is already the latest version. Can you point me in the right direction from here? I wanted to try using the driver you're suggesting.

Specifically, the outuput I get for the sudo apt-get install xserver-xorg-video-radeon command is:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-radeon is already the newest version.
The following packages were automatically installed and are no longer required:
  x11-apps libdrm-nouveau2 libdrm-nouveau2:i386 libxcb-dri2-0:i386
  linux-headers-3.2.0-60 linux-headers-3.2.0-60-generic
  libwayland-ltss-server0 libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386
  x11-session-utils libc6-i386 lib32gcc1 x11-xfs-utils dkms libxrandr-ltss2
  xinit libfs6 libxcb-xfixes0 libwayland-ltss-client0 libllvm3.3
  libllvm3.3:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded. 

---

### Post by mastablasta on 2014-05-22
you are using old kernel so you have old drivers (part of kernel) from before the card came out i believe.

here is how to get newer kernel on 12.04: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

14.04 should improve since it has this year's kernel (still not the latest mind you). i am not sure what the latest fglrx is (i think they are at version 14) but this is how you install latest ones manually (after you download them): [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) 

again if you just use 14.04 the latest ones will likely be in the repositories so you could just use additional drivers application.

edit: they are at 14.04 and latest drivers support your card: [http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)
i think if you want to install them it would be good to upgrade the kernel first. but someone more knowledgable should comment on that part..

edit2: if you want to use opensource drivers instead (which i don't think will be necessary) you can upgrade them using Xorg edgers PPA

---

### Post by verymadpip on 2014-05-22
Hi there.
I believe there was some high strangeness regarding AMD drivers (support for some older cards) & Xorg (a new version) with 12.04 which makes things a bit tricky.
If it's not too big a deal for you I'd be tempted to install 14.04 & use the additional drivers utility.

---

