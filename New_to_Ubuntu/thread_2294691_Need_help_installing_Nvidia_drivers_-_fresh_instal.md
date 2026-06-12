---
title: "Need help installing Nvidia drivers - fresh install"
date: 2015-09-12
forum: New to Ubuntu
---

### Post by hydrizl on 2015-09-12
Hello everyone. So I just installed ubuntu 12.04 lts on my laptop as I need to use the c compiler for my programming class. Anyway, my laptop has both intel onboard graphics and a nvidia 950m card. I just did a fresh install and installed the updates via the update manager.

I am not sure how to approach installing nvidia drivers and using them over my onboard graphics for games on steam, so any insight would be appreciated. Thanks.

---

### Post by Frogs Hair on 2015-09-12
Hello and Welcome

I haven’t used 12.04 for a while but the additional drivers utility should offer various driver options for Nvidia. The the path to the utility has changed a bit since 12.04 so try system settings first.

---

### Post by hydrizl on 2015-09-12
Thank you for the reply. So when I scan with the additional drivers utility, it says no proprietary drivers are found on this system. I'm really confused as to why it says so.

---

### Post by hydrizl on 2015-09-12
Well after doing some more research and getting a better understanding of linux in general (hopefully!), it looks like I have an Optimus GPU and it supposedly isn't supported official by Nvidia yet. This also explains why when I boot into windows my laptop has to switch between integrated graphics and the dedicated card depending on what I'm doing. The bumblebee project appears to be a solution :redface:

---

### Post by mörgæs on 2015-09-12
The 950 m is a new graphics processor so you will be better off with the newest of software. I would go for 15.04 or maybe 15.10 (beta). 

When 12.04 was released the 950 was not even on the market.

---

### Post by grahammechanical on 2015-09-12
Nvidia was very, very slow providing a Linux driver for its Optimus technology. Ubuntu 14.04 was the first version that provided a Nvidia driver that had any kind of support for Optimus.

Even now, do not expect automatic switching between the Intel and Nvidia adapters. You will have to use the Nvidia xserver settings utility to switch. It will be installed at the same time as the driver. Or install Prime Indicator

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Or, Bumble bee which provided open source drivers for Optimus long before Nvidia started work on a Linux driver.

Regards.

---

### Post by hydrizl on 2015-09-14
Thanks for the replies, I am going to install a newer version of Ubuntu as suggested (14.04) and see if I can get Prime indicator working. I really don't need to play games on the OS as I just need it for programming, but I think this is more for my curiosity/learning than anything.

---

### Post by dino99 on 2015-09-14
i suppose 14.04 will not provide a compatible driver for 950m
install that ppa  [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa) update & install nvidia-355, then deactivate the ppa & update again

---

### Post by hydrizl on 2015-09-14
> **dino99 said:**
> i suppose 14.04 will not provide a compatible driver for 950m
install that ppa  [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa) update & install nvidia-355, then deactivate the ppa & update again
Could you give me a command line approach or instruction approach to doing this please. I have an idea how, but I want to be sure before putting commands incorrectly and possibly creating more problems.

---

