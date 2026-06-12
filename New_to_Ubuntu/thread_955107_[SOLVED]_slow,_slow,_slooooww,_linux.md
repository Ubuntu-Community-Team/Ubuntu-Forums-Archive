---
title: "[SOLVED] slow, slow, slooooww, linux"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by WriteGirl on 2008-10-21
I installed Ubuntu about a month ago on my laptop, and everything I read about it said that it was in general a lot faster than windows and didn't slow slow down like windows. I didn't have any problems at first but firefox has been loading slower and slower and now practically every time I try minimize it or try to use another program simultaneously, I have to use force quit or wait for ten minutes. OpenOffice.org stutters when I type too fast in it. I really like Linux, but this is frustrating. The desktop computer I have that runs off the same internet, but uses windows is working significantly faster.

Anyone have an idea why this is happening? I know this is a really general question, so if you have any suggestions of where to start looking, that would be awesome.

---

### Post by david_lynch on 2008-10-21
> **WriteGirl said:**
> I installed Ubuntu about a month ago on my laptop, and everything I read about it said that it was in general a lot faster than windows and didn't slow slow down like windows. I didn't have any problems at first but firefox has been loading slower and slower and now practically every time I try minimize it or try to use another program simultaneously, I have to use force quit or wait for ten minutes. OpenOffice.org stutters when I type too fast in it. I really like Linux, but this is frustrating. The desktop computer I have that runs off the same internet, but uses windows is working significantly faster.

Anyone have an idea why this is happening? I know this is a really general question, so if you have any suggestions of where to start looking, that would be awesome.
That's odd. Did everything suddenly start running slowly, or did it happen all at once? Could be hardware going bad, or another user (are there other users?) running a cpu hog...

---

### Post by skompier on 2008-10-21
Sounds like is could possibly some process hogging CPU time. Look at System>Administration>System Monitor and see if anything is maxing out your CPU.

---

### Post by Nxion on 2008-10-21
> **WriteGirl said:**
> I installed Ubuntu about a month ago on my laptop, and everything I read about it said that it was in general a lot faster than windows and didn't slow slow down like windows. I didn't have any problems at first but firefox has been loading slower and slower and now practically every time I try minimize it or try to use another program simultaneously, I have to use force quit or wait for ten minutes. OpenOffice.org stutters when I type too fast in it. I really like Linux, but this is frustrating. The desktop computer I have that runs off the same internet, but uses windows is working significantly faster.

Anyone have an idea why this is happening? I know this is a really general question, so if you have any suggestions of where to start looking, that would be awesome.

Well first of all, how old is the laptop and what are the specs? Do you get any error messsages at all? Also it could be that the driver for the video might not be loaded. Can you run these commands for us and post the output?

```
lspci
```

and

```
cat /etc/X11/xorg.conf
```

and

When you go to System>Admin>Hardware Drivers. Does anything show up in the list?

---

### Post by eternalnewbee on 2008-10-21
Could be an issue with your hardware. what are your system specifications?
___________________________________
Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by fenian on 2008-10-21
When you begin to notice the slowdown open a terminal and enter this command....

> top

it will list all programs that are running with the one using the most cpu at the top.Which will give you more of an idea where the problem is.

---

### Post by WriteGirl on 2008-10-21
Firefox started slowing down over a period of time, and it wasn't until the last few days that I've had to use force quit. OpenOffice.org seemed slow when I used it in the beginning, but I haven't been using it regularly until this week, so it could have bee fie originally.

My CPU history is telling me that I'm using about 40-45%.
The memory is at 62%, which seems really high, from what I know.

I'm running the commands from above now.

---

### Post by WriteGirl on 2008-10-21
My laptop's about three years old, I think. It's a compaq nc6000.

I got this from ```
lspci
```

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

```

and from ```
cat /etc/X11/xorg.conf
```

```
 xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

For hardware drivers, I have Atheros Hardwar Access Layer and support for Atheros 802.011 wireless LAN cards

---

### Post by Yashiro on 2008-10-21
Have you renamed your computer recently, and did this slowdown appear after this change?

---

### Post by WriteGirl on 2008-10-21
I haven't renamed my computer. One thing I just thought of is the updates that are shown in teh upper right hand corner. There's usually at least one or two every day; is that a normal amount? Unless they look completely superfluous, I usually install them.

---

### Post by patrickballeux on 2008-10-21
You graphic card is not configured at all, so you are probably running in vesa mode which would explain why everything is so slow...  

I saw that you have an ATI card...  Then you have several options:

1- Use the open source driver
2 - Use the driver from EnvyNG
3 - Download the latest from ATI Site.

You should use EnvyNG since it will provide you with a recent version of the proprietary driver.  In Synaptic, look for envyng, install it.  Then in your "Application - System Tools - EnvyNG", follow the instruction to install the grapghic driver.

Reboot, and it should be fast, fast, fast...

Good luck

---

### Post by linux2.6.24-19-generic on 2008-10-21
My guess is that your hard drive is taking a dump.  I would get needed files off that drive ASAP.  Then run a diagnostic tool on it.

Could be wrong, but that is what I would do in this situation.

---

### Post by Nxion on 2008-10-21
Give this a try
[URL="http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_latest_EnvyNG_driver_.28ATI_.26_nVidia.29"]
http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_latest_EnvyNG_driver_.28ATI_.26_nVidia.29[/URL]

That should fix the driver problem.

---

### Post by WriteGirl on 2008-10-21
In the Hardware Driver window, it says that the ATI accelerated graphics driver is not in use. Would it help to enable it, or would taht make it worse?

I went to Application - Add/Remove (I'm pretty sure this is the same as system tools?) but the only Envy one was for a sound card and it was Envy24.

---

### Post by Fixman on 2008-10-21
> I went to Application - Add/Remove (I'm pretty sure this is the same as system tools?) but the only Envy one was for a sound card and it was Envy24.

Its not the same. Go to system->administration->package manager.

---

### Post by WriteGirl on 2008-10-21
It's about a hundred times better. Thank you all very much!

---

### Post by Nxion on 2008-10-21
Glad we could help :)

---

### Post by joey-elijah on 2008-10-22
awwwh ^_^ what a lovely thread!

---

