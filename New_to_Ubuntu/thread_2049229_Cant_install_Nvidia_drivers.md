---
title: "Cant install Nvidia drivers"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2012-08-28
I upgraded to 12.10 today. I didnt knew that its not out yet... Now I have 2 Problems:

I cant install the Nvidia Drivers with Synaptic it says that it cant install dependencies xorg-video-abi-11 or xorg-video-abi-12 ?

The second thing is that i cant access the System Configuration using the menu. It says Opening System config .... but closes automatically after a few seconds without showing errors.

Can anyone help?

---

### Post by khelben1979 on 2012-08-28
Have you tried the nVidia drivers from nVidia.com? 

If you're a linux newbie I wouldn't recommend it, though. Since the nVidia driver will break if you ever decide to upgrade the Ubuntu Linux kernel by your usual Ubuntu updates system, but you should be aware that it's an option to consider if the conflicting driver by the Ubuntu installer system doesn't work out for you, or... consider going for an older version of Ubuntu, that way you got a system which will not cause these problems for you, much easier.

---

### Post by phibxr on 2012-08-28
This shouldn't really be in Absolute Beginner Talk since 12.10 still hasn't reached Beta yet.

Your issue, however, is caused by the NVIDIA drivers not being compatible yet with the X version that 12.10 ships.

The same goes for the AMD Catalyst drivers, and hopefully compatible drivers will be released from NVIDIA and AMD before October when 12.10 is released.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672")

> The move to xserver 1.13 is what brought the new API version. We'll have to wait until AMD provides a 1.13 compliant driver, which typically occurs late in the cycle but some time before final freeze.

---

### Post by critin on 2012-08-28
> Can anyone help?

Install 12.04.  Is that what you upgraded from?   It's the latest and it's stable.  You can't fix 12.10 at this time unless you're willing to test it and put up with it not working.  There are no work-a-rounds for certain things, like nvidia, that creates its own drivers.

---

### Post by khelben1979 on 2012-08-28
What nVidia card or chipset do you got installed? Once you know that, you can check on [http://www.geforce.com/drivers]("http://www.geforce.com/drivers") to see if and when the graphics drivers are available for the card or chipset that you got.

---

### Post by NikTh on 2012-08-28
> **Krabby.Linux said:**
> 

Can anyone help?

Hi ,
actually nobody can help with an Unstable version. Maybe it would be better to post your problem here -->   [http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416)
Thank you

---

### Post by kaldor on 2012-08-28
There have been issues in 12.10 with the NVIDIA drivers lately due to (I believe, at least) new X versions being introduced. Your best bet is either to use the default Nouveau driver with 12.10 and wait a while for a fix, or reinstall Ubuntu 12.04 if you need stability.

Ubuntu 12.04.1 just came out. Download this instead of using the older 12.04 release if you want to save time on updates and configuration.

---

### Post by pqwoerituytrueiwoq on 2012-08-28
there is a fix for the x server issue in the latest driver but you would have to install it manually from nvidia
guide for latest driver
[http://www.blogsolute.com/install-latest-nvidia-driver-linux-mint/23836/](http://www.blogsolute.com/install-latest-nvidia-driver-linux-mint/23836/)
edit: the latest driver is is the xswat ppa now

---

### Post by Kirk M on 2012-09-03
Here's the link to the original bug report that states the problem with the "nvidia-current" (and ATI as well) is currently incompatible with the latest Xorg kernel driver in 12.10.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1033222](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1033222)

Just for info's sake.

---

