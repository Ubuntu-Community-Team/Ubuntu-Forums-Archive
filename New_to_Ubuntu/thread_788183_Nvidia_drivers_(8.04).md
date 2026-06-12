---
title: "Nvidia drivers (8.04)"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by William S on 2008-05-09
Hey!
I have a laptop with a Nvidia video card, however enabling the restricted in the hardware menu just kills the GUI, but it works without it enabled. 
It worked all nicely in 7.10 (in my opinion 8.04 is just half finished, had loads of issues with x-server there which didn't exist in 7.10)

---

### Post by TheLions on 2008-05-09
ok. download drivers from NVIDIA page and install it or even simpler way, install Envy!

---

### Post by William S on 2008-05-12
GUI still doesn't work with the drivers from Envy. 
It says no screens found when the driver is enabled.

---

### Post by barney385 on 2008-05-12
Which Nvidia card are you running?

---

### Post by alienexplorers on 2008-05-12
In Envy did you let it select the driver for you?  If so it may have selected the wrong driver.  On my system I had to select the manual install and selected the 96.xx.xx driver which is the nvidia-glx driver.  I found the nvidia-glx-new driver would not work on my video card, so I had to revert to the plain glx driver.

---

### Post by barney385 on 2008-05-12
> **alienexplorers said:**
> In Envy did you let it select the driver for you? If so it may have selected the wrong driver. On my system I had to select the manual install and selected the 96.xx.xx driver which is the nvidia-glx driver. I found the nvidia-glx-new driver would not work on my video card, so I had to revert to the plain glx driver.
 
Which Nvidia card are you guys running?
 
I've got a M8600GT 512mb on the way and would like to know what you're using.
 
Thanks.

---

### Post by alienexplorers on 2008-05-12
I am running as stated in my sig line a Nvidia GeForce FX5200 video card.  Quite old, but works well with Ubuntu.  In fact my whole system is quite old.

---

### Post by barney385 on 2008-05-12
> **alienexplorers said:**
> I am running as stated in my sig line a Nvidia GeForce FX5200 video card. Quite old, but works well with Ubuntu. In fact my whole system is quite old.
 
Thanks for responding. I'm just curious about any issues with the newer 8000 cards there might be. I think the one I'm getting is OK, not sure about the M8800 though.
 
 
:mad:

---

### Post by William S on 2008-05-13
I am running GeForce 8400 M GS
And why is 8.04 so damn buggy? I also have issues changing screen resolution with my stationary PC and that pc has an ATI.

---

### Post by Xiong Chiamiov on 2008-05-13
I had a hell of a time with getting my card to work (7600 GS).  The solution, based upon [this post]("http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847"), was to use the [newest beta release of the NVIDIA drivers]("http://ubuntuforums.org/showpost.php?p=4946751&postcount=16"), which are fixed for the latest kernel.

---

### Post by bumanie on 2008-05-13
> **William S said:**
> I am running GeForce 8400 M GS
And why is 8.04 so damn buggy? I also have issues changing screen resolution with my stationary PC and that pc has an ATI.

Very unfortunate that you are having this trouble. I have an nvidia 8600gt and it works fine with the hardware driver. Personally, I have found hardy to be less bug ridden than gutsy was, but I have seen others say the same thing about hardy. All I can guess at, is that there is some other part of your system (bios, mobo chipset or something else) that is causing a conflict.
You should look up launchpad and see if it is a known issue with the 8400 and whether there is a fix. Also lodging a bug report would be a good idea. The 8400 is still a fairly recent card and should work well. The only other way is to download off the nvidia site and install via console and closing down xserver. The problem with this method is that you have to reinstall the driver when there are kernel updates.

---

