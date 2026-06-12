---
title: "installation with older NVIDIA graphics card (GNOME previously failed with Debian)"
date: 2021-04-28
forum: New to Ubuntu
---

### Post by ange-p on 2021-04-28
I have a Lenovo Thinkpad T540p from about 2014 which I am currently running Debian on (Linux only, no dual boot) and I would like to change to Ubuntu. 

When I originally installed Debian years ago I had major problems, bricked the machine due to a BIOS bug. Long story short I eventually got it all running and have my BIOS upgraded and set up correctly (ie Secure Boot off, Intel Rapid Start Technology disabled, UEFI/Legacy Boot Priority=Legacy First, OS Optimised Defaults Disabled etc).

The problem that I could not sort out was the graphics card. I have a NVIDIA GeForce GT 730M and an Intel integrated GPU. And GNOME3 failed to load during the Debian install. I did a lot of troubleshooting and I can't remember all but I don't think it supported my driver version, and eventually discovered I have NVIDIA Optimus technology and tried Bumblebee, but this did not work either.  The only way I could get it working was to use xfce4 desktop - which is fine because I am programming and don't need any advanced graphics. 

My question is will the latest 20.04 work for my machine in terms of the desktop environment, is there anything I need to do before upgrading to prepare for this?
I noticed in a recent Lenovo Ubuntu installation guide for their recent models it says to go into the BIOS and change the Graphics mode to Hybrid graphics to avoid graphical issues during installation. I don't know whether this would be what I need to do to get things working but I looked in my BIOS and I don't have any config options for graphics anyway.

I'm also considering Xubuntu, will this work for me, and similarly is there anything I would need to know regarding the GPU etc before installing?
(I noticed someone upgrade with a screen that listed graphics devices and that it automatically installs the NVIDIA drivers - I'm not sure whether this is what I should be doing.)

I haven't tried the LiveCD of either Ubuntu or Xubuntu yet - will this let me see if it can work - or is there a risk that if it doesn't the LiveCD could hang/break something on my machine?

I also have an external monitor connected that I work from - not sure if this is relevant to the problem but mentioning it anyway - it works fine with my Debian/xfce system.

Also - when I have previously installed versions of Debian it says firmware is required for wifi and I have to put a USB in with a file in it. Is this something I may come up against installing Ubuntu or Xubuntu.

Thank you in advance.

---

### Post by ActionParsnip on 2021-04-29
If you need firmware then put the file in /lib/firmware
It's it's a Broadcom WiFi then there is a tool for that in Ubuntu

---

### Post by grahammechanical on 2021-04-29
When we install Ubuntu we get an option to install  non-free third party software. Debian does not give you that option. If we choose to install non-free software we get among other things, proprietary video drivers. In your case it will be an Nvidia driver.

There is something about hybrid graphics you need to understand. The Nvidia drivers for Windows will automatically switch between Intel graphics and Nvidia graphics. The Nvidia drivers for Linux do not automatically switch. This problem was raised on this forum many years ago when machines with that type of hybrid graphics was the latest idea to prolong battery life.

The Ubuntu live session does not come with proprietary video drivers. It is possible to install them during a live session.

Regards

---

### Post by tea for one on 2021-04-29
> **ange-p said:**
> I haven't tried the LiveCD of either Ubuntu or Xubuntu yet - will this let me see if it can work - or is there a risk that if it doesn't the LiveCD could hang/break something on my machine?

A live session (preferably with a USB rather than a DVD) will not break anything on your PC if you are simply exploring Ubuntu.
As long as you do not play around with your existing Debian OS, then no damage will ensue.

It's an ideal, non-intrusive way to test graphics, keypad, sound, wifi, internal card readers etc.

---

### Post by ange-p on 2021-04-29
> **grahammechanical said:**
> When we install Ubuntu we get an option to install  non-free third party software. Debian does not give you that option. If we choose to install non-free software we get among other things, proprietary video drivers. In your case it will be an Nvidia driver.

There is something about hybrid graphics you need to understand. The Nvidia drivers for Windows will automatically switch between Intel graphics and Nvidia graphics. The Nvidia drivers for Linux do not automatically switch. This problem was raised on this forum many years ago when machines with that type of hybrid graphics was the latest idea to prolong battery life.

The Ubuntu live session does not come with proprietary video drivers. It is possible to install them during a live session.

Regards

Thank you everyone. My recollection is that previously I should not install proprietary drivers (or any graphics drivers as I couldn't get nouveau to work either), and just not use the NVIDIA card as this caused problems previously, and I don't need hybrid graphics. And if the NVIDIA drivers for Linux don't automatically switch then I don't need to use the hybrid graphics / NVIDIA discrete card anyway. (I had a look back at the previous forum posts and this was my anguish back then too). 

From what I now understand, during an Ubuntu or Xubuntu installation, there will be an option to install extra graphics drivers for which I should NOT do, so that I just stick with the Intel graphics only. Is this correct? Does this mean GNOME will then load, or should I still be just sticking with xfce for it to work?

Thanks.

---

### Post by ange-p on 2021-04-29
> **tea for one said:**
> A live session (preferably with a USB rather than a DVD) .


Thanks - why preferably with a USB than a DVD?

---

### Post by tea for one on 2021-04-30
> **ange-p said:**
> Thanks - why preferably with a USB than a DVD?

I prefer using USB principally:-

Quicker to prepare with a chosen ISO
Faster booting and operation
Ability to create persistent storage
Easy to partition
Many PCs lack CD/DVD drives
Useful to keep as a troubleshooting device

---

### Post by poorguy on 2021-05-03
> **grahammechanical said:**
> When we install Ubuntu we get an option to install  non-free third party software. Debian does not give you that option. If we choose to install non-free software we get among other things, proprietary video drivers. In your case it will be an Nvidia driver.

Regards
Is that only for **Ubuntu** or is that for **Ubuntu** and **Ubuntu official flavors.**

I recently installed **Xubuntu 20.04.2** and **checked the option to install  non-free third party software **hoping to get an** Nvidia proprietary video driver** and nothing[B] no options for any additional non-free third party software.
[/B]

Thanks


My apologies to **ange-p** for asking my question in your thread.

---

### Post by ange-p on 2021-05-26
Just updating that I ran the Live CD and tested and everything worked, so I went ahead and installed Ubuntu, and I did not choose to install any extra drivers - and it all works fine. Thank you.

---

