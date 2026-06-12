---
title: "Ubuntu in general all versons"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by James_Robinson on 2014-04-27
I have a question about how to choose the right video card, for my system. I have been using ubuntu 12.04 Lts for a few yrs now. and been looking on pages on the net like  X.org and Opengl. tell me dose the normal end user like my self that uses this kind of system have to learn those two to install a video driver in order to make a online or windows game work. were dose one start first on this kind of problem ???. also the chipsets on my motherboard can they be updated to or have to????.

---

### Post by grahammechanical on 2014-04-27
When we install Ubuntu whatever the version or flavour then Ubuntu will install a video driver at the same time. Ubuntu comes with an open source video driver as a default. If at the start of the install process with tick "Install third party software," then Ubuntu will install a proprietary video driver appropriate for our video card. If we do not tick to install third part software, then the open source video driver will be used instead. Once Ubuntu is installed we can use a Utility called Additional Drivers to change video drivers.

Right now I am using Ubuntu 14.04 with an Nvidia GBT220 graphic card and Additional Drivers is offering me 1 open source video driver and 4 versions of the Nvidia proprietary video driver.

I have not had to learn anything about Xorg or OpenGL ever since I started using Ubuntu back in 2007. Did you need to know anything about Xorg and OpenGL in order to install and use Ubuntu 12.04? There you are. You already know the answer.

Online games and Windows games are something else. Windows programs will not run in Linux. If you cannot get a Linux version of the game then you need to look at something called Wine. But do not expect miracles.

[http://www.winehq.org/](http://www.winehq.org/)

Games demand powerful hardware. The games developers are always pushing the need for more powerful hardware. And online gaming, I should imagine, would require fast data transfer rates.

Depending on the motherboard it might be possible to upgrade to a more powerful graphic adapter but check first if there are Linux video drivers for it. I doubt very much if we can upgrade motherboard chipsets as they are soldered onto the motherboard.

Regards.

---

### Post by James_Robinson on 2014-04-27
i don't have a videocard in my system now just but onboard chipset. but i was going to get one soon and that is why i wrote that post. and was not sure on how to pick the right card. some people told me online the ati works good and Nvidia works good. i have used wine before though, and that works good on some windows games with a bit of tweeking

---

### Post by verymadpip on 2014-04-27
```
If at the start of the install process with tick "Install third party  software,"
then Ubuntu will install a proprietary video driver  appropriate for our video card.
If we do not tick to install third part  software, then the open source video driver will be used instead.
```

At the risk of thread drift, this has never happened for me.
I always tick the 3rd party software box & it has never installed a proprietary driver for me.

I quite like it that way, but that's just me.

Ooops, sorry I've used code tags instead of quoting...can that be fixed?

---

### Post by waynefoutz2 on 2014-04-27
> **James_Robinson said:**
> i don't have a videocard in my system now just but onboard chipset. but i was going to get one soon and that is why i wrote that post. and was not sure on how to pick the right card. some people told me online the ati works good and Nvidia works good. i have used wine before though, and that works good on some windows games with a bit of tweeking


Go with Nvidia. You pay a little more, but you'll make out better in the end. ATI drops support for their older hardware. I've been burned twice by buying laptops with ATI GPUs in them.

---

