---
title: "having trouble with nvidia drivers and some concepts."
date: 2012-04-30
forum: New to Ubuntu
---

### Post by RageRiot on 2012-04-30
Hi, 

 I'm new to the world of linux although I've known about it since I learned about PC's with windows about 10 years ago. yes I'm a born n bred windows user but I've really wanted to get into the *unix for a long time.

   My current PC which I built and configured my self at the start of 2009 is running windows 7 but I was given a a desktop so decided to put ubuntu on it so I can get started learning about it.  

The desktop I have ubuntu installed on is a Dell Dimension 4600,  I cant access the configuration page now from dell because it appears they have taken the information down so I believe the following information might help to determine what is in my system

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P AGP Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:00.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
02:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```the first thing I tried was the 'additional drivers' window which was empty then I got the following driver from nvidia.com - NVIDIA-Linux-x86-173.14.31-pkg1

I ran that and the installer said it failed on the pre-install script but asked if I wanted to continue, I didnt at first but then decided to go for it but then the PC only booted to shell.
I tried nvidia-current and that did the same thing. 
I did run the nvidia-xconfig after both of the previous attempts.


At some point I came across the command jockey-text --no-dbus -l (still not sure what commands actually do yet like I do with windows i.e ipconfig but I know I've got alot to learn) that outputs this:

```
WARNING:root:modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

WARNING:root:modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

WARNING:root:modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

WARNING:root:modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

WARNING:root:modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

WARNING:root:modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

WARNING:root:modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

WARNING:root:modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

WARNING:root:modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

WARNING:root:modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

WARNING:root:modinfo for module wl failed: ERROR: modinfo: could not find module wl

WARNING:root:modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

WARNING:root:modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

WARNING:root:modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

WARNING:root:modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
```Should I worry about those warnings ?

As well as graphics card drivers should I need some type of AGP driver first, against somthing I was used to with windows was having to install agpgart driver before the GFX card driver.

Since I'm so new to linux maybe I'm going about stuff the wrong way.

Thanks 

RageRiot

---

### Post by papibe on 2012-04-30
Hi RageRiot.

I'm afraid at this moment, the oldest version of the driver (173 and 93) are not compatible with the new versions of Ubuntu (actually any Linux distribution using an up-to-date versions of the Xorg - the windows manager).

This may change in the near future if Nvidia decides to update their legacy drivers to support the current version of X.

For now, I would recommend using the default open source driver, called nouveau. This days it is working pretty well supporting Nvidia cards.

Regards.

P.D.: sources: [Bug #948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053") and [Bug #990539]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/990539").

---

### Post by RageRiot on 2012-04-30
is it worth going back to a previous version to get it to work? 

my main concern over this is the system seems slugish, windows a stuttery although is isnt terrible it just may end up becoming a deterrent from my ubuntu desktop.


is it correct that the nouveau is only 2D? 
I'm guessing since I disabled the nvidia-current driver it defaults back to nouveau? is there any settings or optimization I can perform for this driver?

what about system drivers? / (chipset etc?)

---

### Post by audiomick on 2012-04-30
I believe the standard Ubuntu drivers are 2D, at least on nVidia cards, but I am not sure.

You have asked a couple of times about other drivers. One of the nice things about ubuntu and Linux in general is that you don't really have to worry about drivers for the most part. The only exceptions are things like nVidia and other Graphics cards that want proprietary drivers that can't be distributed with the OS. Normally, if you need to add drivers to an ubuntu system, the hardware driver utility will tell you, and offer to get them for you.

---

