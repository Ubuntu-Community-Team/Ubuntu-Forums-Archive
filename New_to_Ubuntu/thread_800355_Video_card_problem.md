---
title: "Video card problem"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Bubblebeard on 2008-05-19
Hello all,

I am very new to Linux and am trying to install the Battle for Wesnoth (games without any advanced graphics work fine, but other than that none do). I installed all the prerequisite packages and downloaded the source for Wesnoth. When I tried to configure Wesnoth (with ./configure), it said:

checking for PNG support in SDL_image... no
configure: error: *** Either your test image has vanished, or SDL_image has no PNG support!


So I tried the Synaptic Package Manager, and it installed Wesnoth, but now when I run Wesnoth the terminal tells me:

20080518 08:22:49 error display: Could not initialize SDL: No available video device
Could not initialize video. Exiting.

I think it is something to do with my graphics card not being installed properly but I don't know... it seemed to install fine and when I go to System-Administration-Hardware Drivers it lists "NVIDIA accelerated graphics driver (latest cards) [Enabled] Check [Status] In use"

One other thing I noticed was that when I ran lspci it said "Display controller: Intel Corporation 82845G/GL" - that was my old graphics card so maybe it thinks it should use that?


root@david-desktop:/drivers/cdrom0# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)



I have checked all other posts and tried numerous things but can't get it to work. Can anyone help me? Any help would be appreciated!

---

### Post by Bubblebeard on 2008-05-19
Does nobody know?

---

### Post by skillet on 2008-05-19
how did you install libsdl? did you compile that from source as well? if you did you might want to look at what options you can compile into it. maybe something like --with-png or something to that effect or look for a package within synaptic. it makes sense to install with the package manager so you get all future updates/bugfixes.

---

### Post by Bubblebeard on 2008-05-21
I tried it both ways but it didn't work either way.  SDL image said to install libpng and zlib, which I also did, but the same thing happened both methods of installation.

---

### Post by Bubblebeard on 2008-05-27
Hi,

just for anyone with the same problem who is later reading this I solved it.

Reinstall Ubuntu, get an internet connection if you don't have one, update ubuntu, restart, go to your hardware drivers from the menu, check to enable and install the one for your card, restart, go to the synaptic package manager, check wesnoth and whatever campaigns and music etc, apply, and you win!

---

