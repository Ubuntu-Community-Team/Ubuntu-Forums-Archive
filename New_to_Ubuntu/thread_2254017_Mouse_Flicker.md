---
title: "Mouse Flicker"
date: 2014-11-24
forum: New to Ubuntu
---

### Post by Pougan on 2014-11-24
So we are switching to Ubuntu 14.10 at my office and I'm largely working well, however I have an extremely annoying problem that I've been trying to resolve for a few weeks now to no avail. I have an HP 8200 Elite Tower with Intel Integrated Graphics and a Radeon HD 6450 video card. I use both to run 4 total monitors. I'm using the default open source radeon and intel drivers which are working most of the way, but for some reason on the monitors attached to the Radeon Card my mouse flickers pretty constantly (the screen doesn't flicker, just the mouse cursor). It does not flicker at all on the monitors attached to the intel integrated graphics. I've tried installing the proprietary drivers both from the Ubuntu repositories and directly from ATI's website, but when I do that the two monitors attached to the Intel graphics card do not work (but the flickering disappears!). When I use the proprietary drivers and aticonfig --initial, it sets up the ati card just fine and then I add the intel screen, monitor, and device and as far as I can tell everything is setup properly but then X will not start. I've also tried using X -configure with the open source drivers to generate the xorg.conf file but even that causes X not to start! The open source drivers only work if I do not have an xorg.conf at all.

I've also tried putting another Radeon card in and disabling the intel integrated graphics (I've tried both a 1x 5450 card and another 6450 in the 4x slot) but I could only get 3 monitors total working and for some reason the 4th monitor would not work.

I also thought it might have to do with the virtual guest additions in my Windows 7 Virtual Box VM, but it does it even with virtual box closed and my VM off.

I've also seen some things online about an Unknown monitor needing to be disabled, but I do not have that.

At this point I'm just living with the mouse flicker because I need to get some work done, but just wondering if anyone has any suggestions for getting rid of the mouse flicker or getting the proprietary drivers working with the intel integrated graphics.

Thanks!

---

### Post by Pougan on 2014-11-24
Results of lspci if that helps at all:
> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Q67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]


---

### Post by MrSteve on 2014-11-24
have you tried intels own GPU driver installer
this link is for 14.04 LTS but should work with 14.10 ...

[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux)

if that fails then it might be worth while trying a new mouse, that worked for me with a similar problem ...

---

### Post by Pougan on 2014-11-24
It looks like 1.0.7 of the intel installer is available but it targets 14.04 and when I try to run it it says my distribution is not supported. 14.10 support is due in December/January :(.

---

### Post by MrSteve on 2014-11-24
may i ask if your systems are office systems why are you not using the LTS (Long Term Support) version of ubuntu ?
LTS is supported for 5 years the version you are installing is supported for 9 months ...

---

### Post by Pougan on 2014-11-25
At the moment we are only installing Ubuntu on our developer machines, so under normal circumstances updating every 6 months shouldn't be a problem. But if I'm unable to get my video drivers working properly under 14.10 I may consider dropping back to 14.04 LTS for my sanity's sake.

---

### Post by Pougan on 2014-12-03
Just FYI, I ended up getting a GTX 750 video card that supports 4 monitors by itself. That with the proprietary Nvidia drivers fixed the problem. Not really a solution, but I'm not going to go crazy because of a flickering mouse pointer anymore :).

---

