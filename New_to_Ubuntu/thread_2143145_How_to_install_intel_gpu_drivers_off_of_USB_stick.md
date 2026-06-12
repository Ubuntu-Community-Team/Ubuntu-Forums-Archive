---
title: "How to install intel gpu drivers off of USB stick?"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by wubinoob2 on 2013-05-08
I can only boot to terminal. 

I have the linux driver for the intel gpu on a flash drive.

How do I, via terminal get the Linux driver released by intel onto the computer?

I tried mounting the USB stick, but I don't know how to copy the file, which is blue, to the os for installation?

---

### Post by mastablasta on 2013-05-08
intel GPU driver is already included in the kernel. you do not need to install it.

otherwise unpack the file and follow the instructions in the readme file inside it.

what are your system specs? perhaps there is a better, simpler solution to your problem.

---

### Post by fantab on 2013-05-08
Unlike other Graphic driver, Intel grapics work 'out of the box' in Ubuntu. I don't think it could be "driver" issue. You have to give us more details. 
What version of Ubuntu you have? Is this a recent install? Is there any other OS installed? Sometimes reinstalling Ubuntu is the simplest solution.

---

### Post by Impavidus on 2013-05-08
According to [this thread]("http://ubuntuforums.org/showthread.php?t=2143108&p=12638349") it's a freshly installed wubi 12.04.

---

### Post by wubinoob2 on 2013-05-10
[http://www.intel.com/products/motherboard/D201GLY2/configs.htm](http://www.intel.com/products/motherboard/D201GLY2/configs.htm)

Im hoping that's sufficient in terms of main specs.

Addenum:
Running off IDE 160GB 
Sata cd/dvd
Windows xp sp3 uptodate

---

### Post by wubinoob2 on 2013-05-10
Im hoping it's a gpu driver issue cause I'm out of ideas.

The readme file for the intel driver is inaccessible it seems without using Linux/Ubuntu...

---

### Post by deadflowr on 2013-05-10
What's the output from 
```
lspci | grep VGA
```

Because the spec page doesn't say what the graphics cards specs are, but basing it on the chipset, it's not intel but SiS.

---

### Post by wubinoob2 on 2013-05-11
Oh that makes sense. 

More info:

SIS 661/741/760 PCI/AGP OR 662/761GX PCIE VGA DISPLAY ADAPTE REV 04

---

### Post by deadflowr on 2013-05-11
Unfortunately, unlike other graphics card makers, SiS doesn't supply support for linux drivers.
All support, as I think, is done solely by the open-source community.

The best place I've found to get a SiS card's config set to work well, is here
[URL="http://www.winischhofer.net/linuxsispart1.shtml"]
http://www.winischhofer.net/linuxsispart1.shtml[/URL]

Of course, it goes without saying, I'm not sure how well this will help with a wubi install.

---

### Post by wubinoob2 on 2013-05-11
Hey dead flower thanks for helping throughout the way. I came up with the same. It seems sis drivers are pita when it comes to Linux drivers.
In the meantime I was tinkering and tinkering and I ran the following command while stuck in terminal xserver/xorg sis drivers (I don't recall the exact line)
And update cmds. After a restart I finally got to access the GUI. However I have the vertical lines issue which gets cured if I run a lower res.

My question now lies with a couple things.
Intel supports this board with a Linux graphics driver. I have it on my USB key, and it's just an upload of the link that we both came up with from winhouser.
I would like to know how to install this file from either a GUI method or a terminal method.

If possible I would appreciate it if it could be somewhat guided at least command wise.

---

### Post by blind3d on 2013-05-11
Well, I would suggest creating a custom ubuntu live iso, not sure if you can do it with wubi...
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

You can find whatever kernel module / packages are required for install and include them in a custom iso...
Thought I have never done this, this is only a suggestion and should work in theory

---

### Post by deadflowr on 2013-05-11
> **wubinoob2 said:**
> Hey dead flower thanks for helping throughout the way. I came up with the same. It seems sis drivers are pita when it comes to Linux drivers.
In the meantime I was tinkering and tinkering and I ran the following command while stuck in terminal xserver/xorg sis drivers (I don't recall the exact line)
And update cmds. After a restart I finally got to access the GUI. However I have the vertical lines issue which gets cured if I run a lower res.

My question now lies with a couple things.
Intel supports this board with a Linux graphics driver. I have it on my USB key, and it's just an upload of the link that we both came up with from winhouser.
I would like to know how to install this file from either a GUI method or a terminal method.

If possible I would appreciate it if it could be somewhat guided at least command wise.

Don't know if this is helpful, but this closed thread was trying to get that card working
[http://ubuntuforums.org/showthread.php?t=1526038](http://ubuntuforums.org/showthread.php?t=1526038)

---

