---
title: "SiS Graphics Driver Issue on 11.10"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by popisfizzy on 2012-03-18
Hello. I'm basically a complete newbie to Ubuntu, and Linux in general, so I'll try and do as best I can to explain this. I believe I'm having a driver issue, as VLC, the default Movie Player, etc. will only display video when the window is either being resized or repositioned. Otherwise, I get a blank screen. (Video does work on websites, like Youtube, but my guess is that Flash is just rendering that without any GPU/IGP support).

My graphics card info from lspci is as follows::[INDENT]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
[/INDENT]Now, I've already looked on Google and used the search here to find threads such as this one ([http://ubuntuforums.org/showthread.php?t=1897933](http://ubuntuforums.org/showthread.php?t=1897933)) that explain SiS has basically not made any graphics drivers for Linux (though their site does show one from 2002 for Redhat, if that's any help).

Google brought up this post ([http://askubuntu.com/questions/55892/how-can-i-get-video-working-properly-on-my-shuttle-ss30g2](http://askubuntu.com/questions/55892/how-can-i-get-video-working-properly-on-my-shuttle-ss30g2)) on AskUbuntu which involved some modification to the xorg.conf file. The following will allow video on VLC, etc. to display on my system.[INDENT]Section "Device"
Identifier "Video Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Video Device"
EndSection
[/INDENT]The problem is that it forces me into a weird resolution, and I'm only given two resolution options when I attempt to change it. I also get horizontal white lines on the screen, periodically, especially when moving, modifying, or resizing a window. I know nothing about the xorg.conf file, its syntax, or what it's for, but my main question is: Is it possible to fiddle with this file in such a way that I can get the right resolution for my monitor *and* be able to display video?

Thank you for any help.

---

