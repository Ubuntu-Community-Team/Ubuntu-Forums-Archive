---
title: "Need Video driver for SIS VGA card"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by mattfurlani on 2008-09-22
I supposedly have a Silicon Integrated Systems video card. Another forum member claims their are no proprietary drivers for said card. if someone can prove him wrong I would be very happy and if you could help me get my video card running I also would be very happy. If you need some more information on the specifics of my video card here they are

matt@matt-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by C.S.Cameron on 2008-09-22
Wish I could find a simple method myself.
Found some really complex looking methods searching D201GLY2.
But I got scared off.
Good luck, please let us know if you find something (simple).
There are linux sis drivers on the intel site:
[http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=All&strTypes=All&ProductID=2873&lang=eng&OSFullName=All%20Operating%20Systems](http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=All&strTypes=All&ProductID=2873&lang=eng&OSFullName=All%20Operating%20Systems)
But I can't get them to work either

---

### Post by willca on 2008-09-23
I feel for you man. Hard to find a proprietary linux driver for that card.

Worst case if you cant get an X up with any driver you get from the vendor (if you get any I mean). I would just use vga or vesa in my xorg.conf.

---

### Post by kansasnoob on 2008-09-23
That card does not even seem to be supported by Medibuntu but you could try:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Remember the GPG key!

Then try:

```
sudo apt-get install alsa-firmware
```

I'd also personally install:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video!

Lots of toggles:

[ATTACH]86156[/ATTACH]

[ATTACH]86157[/ATTACH]

Too many for one screenshot!

---

### Post by anewguy on 2008-09-23
I thought those were covered by the xserver-xorg-video-sis package in Synaptics??

Did you try to configure xserver selecting sis as the video chipset?

Dave :)

---

### Post by anewguy on 2008-09-23
Using ndiswrapper, don't the drivers from SiS, found at the following link, work?

[http://www.helpdrivers.com/ingles/listado/panellis.asp?marca=SIS&perif=video2]("http://www.helpdrivers.com/ingles/listado/panellis.asp?marca=SIS&perif=video2")

Dave

---

### Post by mattfurlani on 2008-09-25
> **anewguy said:**
> Using ndiswrapper, don't the drivers from SiS, found at the following link, work?

[http://www.helpdrivers.com/ingles/listado/panellis.asp?marca=SIS&perif=video2]("http://www.helpdrivers.com/ingles/listado/panellis.asp?marca=SIS&perif=video2")

Dave

Which one would i use? i don't really understand what all this means. I'm about linux savy as as a 12 year old understands calculus. So if you could 'stupify' some of this i think it could help me better. I'm kinda treating linux as moving to another country without speaking the local language. So i'm learning as i'm going. I just got this running like a week ago so, bare with my ignorance. i've been without the time and money to buy a dummies user guide.


Another note. What is Xnvidia? i was looking around on my compy and people keep talking about xconfig and xnvidia.

Is that something i need to configure? or is that not compatable with my video card. I don't know how to work anything in the terminal.

---

### Post by anewguy on 2008-09-26
XnVidia is referring to having an nVidia video card - you have SIS.



Forget what I said about using ndiswrapper and the Windows driver from that page - ndiswrapper is  for network cards and I guess I forgot what we were talking about for a moment there! :)

What I would do is the following:

open a terminal window:

Applications/Accesories/Terminal

Then:

(1) cd /etc/X11 <enter>  This will change what is called your working directory (by default it puts you in your "home" folder) to /etc/X11

(2) sudo cp xorg.conf xorg.conf_good <enter> This will make a copy of your existing xorg.conf file so we can experiment without losing a known working copy.  It will ask for a password and this is just your normal log on password.

(3) sudo gedit xorg.conf <enter> This will open the file xorg.conf in a graphical editor so we can make changes.

(4) Click on the "Find" button, enter VESA in the search string and click "Find".  Hopefully it will highlight a line that will look something like the following:

	Driver		"vesa"

(5) Change VESA (whatever it's case) to sis (the quotes must remain)

(6) Click "Save"

(7) Close the editor window

(8) hold down the Ctrl and Alt keys on your keyboard and press the Back Space key, then let go of all keys.  This will restart your X session with the changed xorg.conf file and you will need to log on again.  See if things are any better.

If you can't find "VESA" in the editor, click "Edit" then "Select All", then click "Copy" and post a message back here and paste in the contents you just copied.

Sorry about the previous mix-up - I've been trying to answer some questions people had on wireless and I just got my "wires" crossed! :)

The SIS driver is included in Ubuntu, so it's just a matter of telling the X server to use it.  I'm a little surprised Ubuntu didn't detect that when you installed (maybe it did - if you can't find VESA we'll see).

Dave :)

---

### Post by mattfurlani on 2008-09-28
matt@matt-laptop:~$ cd/etc/x11
bash: cd/etc/x11: No such file or directory
matt@matt-laptop:~$ cd /etc/x11
bash: cd: /etc/x11: No such file or directory
matt@matt-laptop:~$ 


I kinda hit a wall at step one. Help!

---

### Post by Locke_99GS on 2008-09-29
> **mattfurlani said:**
> matt@matt-laptop:~$ cd/etc/x11
bash: cd/etc/x11: No such file or directory
matt@matt-laptop:~$ cd /etc/x11
bash: cd: /etc/x11: No such file or directory
matt@matt-laptop:~$ 


I kinda hit a wall at step one. Help!

Linux is case sensitive. The "X" in the path must be capital.

```

cd /etc/X11

```

---

### Post by mattfurlani on 2008-09-29
> **Locke_99GS said:**
> Linux is case sensitive. The "X" in the path must be capital.

```

cd /etc/X11

```

haha doyoi!

ty

---

### Post by mattfurlani on 2008-09-29
> **anewguy said:**
> XnVidia is referring to having an nVidia video card - you have SIS.



Forget what I said about using ndiswrapper and the Windows driver from that page - ndiswrapper is  for network cards and I guess I forgot what we were talking about for a moment there! :)

What I would do is the following:

open a terminal window:

Applications/Accesories/Terminal

Then:

(1) cd /etc/X11 <enter>  This will change what is called your working directory (by default it puts you in your "home" folder) to /etc/X11

(2) sudo cp xorg.conf xorg.conf_good <enter> This will make a copy of your existing xorg.conf file so we can experiment without losing a known working copy.  It will ask for a password and this is just your normal log on password.

(3) sudo gedit xorg.conf <enter> This will open the file xorg.conf in a graphical editor so we can make changes.

(4) Click on the "Find" button, enter VESA in the search string and click "Find".  Hopefully it will highlight a line that will look something like the following:

	Driver		"vesa"

(5) Change VESA (whatever it's case) to sis (the quotes must remain)

(6) Click "Save"

(7) Close the editor window

(8) hold down the Ctrl and Alt keys on your keyboard and press the Back Space key, then let go of all keys.  This will restart your X session with the changed xorg.conf file and you will need to log on again.  See if things are any better.

If you can't find "VESA" in the editor, click "Edit" then "Select All", then click "Copy" and post a message back here and paste in the contents you just copied.

Sorry about the previous mix-up - I've been trying to answer some questions people had on wireless and I just got my "wires" crossed! :)

The SIS driver is included in Ubuntu, so it's just a matter of telling the X server to use it.  I'm a little surprised Ubuntu didn't detect that when you installed (maybe it did - if you can't find VESA we'll see).

Dave :)

# xorg.conf (X.Org X Window System server configuration file)
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


I think the driver is assigned to 'KDB'? Dunno what KBD is

---

### Post by anewguy on 2008-09-29
As mentioned in our private message exchange, you need to at a minimum add the following after the "Configured Video Device" statement:

driver   "sis"

Then either reboot or restart your xsession with ctrl/alt and backspace.

Also as mentioned, there will probably need to be additional changes, but we'll go one step at a time so we can isolate problems.

Also as mentioned, the server keeps a log in /var/logs/xorg.log.0 (or something similar).  You can review this log (newest info starting from top down) to see if it accepted the driver or defaulted to something else.  Also look for any errors and if found post back here.

Also, for others who may get this same question, let's try to keep everything here so somebody else can see the complete stream.

For recovery, if the xsession fails after the changes or if all you get is a text-mode login prompt, log in as yourself and do the following:

cd /etc/X11 <enter>

sudo cp xorg.conf_good xorg.conf <enter> This assumes you followed previously posted instructions that created this backup file.

reboot or restart your xsession, then check the log file for errors.

Dave :D

---

### Post by mattfurlani on 2008-09-30
> **anewguy said:**
> add the following after the "Configured Video Device" statement:

driver   "sis"

Well, I made the change and rebooted, it reloaded the session fine but my games are still blotchy or do not run. 

I noticed prior to the changes that streaming video off the internet or on the computer works fine. I always thought that the computer needed a functioning video driver to stream videos...

also i spelled it like this

EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"SiS"
EndSection

Section "Monitor"

Wondering if this is also caps-sensitive

---

### Post by anewguy on 2008-09-30
It was using a valid video driver, just not necessarily the one specific to your card, so some things would work.

As far as case goes, it would be a lower case "sis".

As mentioned before, this is probably just a first step.

I would make the change, boot, and if you can log on then copy/paste the file /var/log/Xorg.0.log back here so we can check to see what X really used.

Good luck, and hang in there!

Dave :)

---

### Post by anewguy on 2008-10-01
Another note:  I doubt that a sis video chipset is up to playing a lot of games, particularly if you are using Wine to run them.  I'm not sure, but I don't think any of these were more than mediocre performance/capability wise.

---

### Post by mattfurlani on 2008-10-01
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B]
	[5] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[6] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[7] -1	0	0xe2001000 - 0xe2001fff (0x1000) MX[B]
	[8] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[20] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[21] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B]
	[5] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[6] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[7] -1	0	0xe2001000 - 0xe2001fff (0x1000) MX[B]
	[8] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[23] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[24] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.4.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0x9000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (==) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "2.24.4a" found (new SiS data layout)
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		[http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): DIMM0 is DDR SDRAM
(--) SIS(0): DIMM1 is DDR SDRAM
(--) SIS(0): DIMM2 is not installed
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 332.892 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xE8000000
(--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
(--) SIS(0): VideoRAM: 65536 KB
(II) SIS(0): Using 64960K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
(--) SIS(0): BIOS uses LCDA for low resolution and text modes
(--) SIS(0): No CRT1/VGA detected
(--) SIS(0): Detected LCD/plasma panel (1280x800, 6, non-exp., RGB18 [6cc108])
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
(II) SIS(0): CRT2 gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 665.784 MHz
(--) SIS(0): Detected LCD PanelDelayCompensation1 0x00 (for LCD=CRT1)
(--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(--) SIS(0): CRT2 DDC probing failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 400 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Correcting missing CRT2 monitor HSync range
(II) SIS(0): Correcting missing CRT2 monitor VRefresh range
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using hsync range of 30.00-80.00 kHz
(II) SIS(0): Configured Monitor: Using vrefresh range of 59.00-61.00 Hz
(II) SIS(0): Configured Monitor: Using vrefresh value of 71.00 Hz
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 400.00 MHz
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x720" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (unknown reason)
(II) SIS(0): Not using default mode "1280x960" (unknown reason)
(II) SIS(0): Not using default mode "1280x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (unknown reason)
(II) SIS(0): Not using default mode "1400x1050" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "1360x768" (unknown reason)
(II) SIS(0): Not using default mode "1280x800" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1680x1050" (unknown reason)
(II) SIS(0): Not using default mode "1920x1080" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(--) SIS(0): Virtual size is 1280x800 (pitch 1280)
(**) SIS(0): *Default mode "1280x800" (1280x800) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1280x768" (1280x768) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1280x720" (1280x720) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
(**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
(**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
(**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
(**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
(**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
(**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
(**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
(**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
(==) SIS(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe2100000 - 0xe211ffff (0x20000) MX[B]
	[1] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B]
	[7] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[8] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[9] -1	0	0xe2001000 - 0xe2001fff (0x1000) MX[B]
	[10] -1	0	0xe2000000 - 0xe2000fff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x00009000 - 0x0000907f (0x80) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[22] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[23] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[24] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[25] -1	0	0x00001000 - 0x0000100f (0x10) IX[B]
	[26] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[27] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 2.24.4a
(==) SIS(0): Write-combining range (0xe8000000,0x4000000)
(II) SIS(0): Setting standard mode 0x16
(II) SIS(0): RENDER acceleration enabled
(II) SIS(0): Framebuffer from (0,0) to (1279,12990)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
		32 8x8 color pattern slots
(--) SIS(0): CPU frequency 1400.09Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	183.6 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	184.0 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	57.1 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	184.3 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	186.7 MiB/s
(--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): Default Xv adaptor is Video Overlay
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
(==) RandR enabled

---

### Post by anewguy on 2008-10-01
Okay, it's using the sis driver now.  Try looking under system/preferences/screen resolution and see if you can change your resolution to something you like better.  Be forewarned - usually the first few attempts at this aren't pretty, and you may be in a position where you will just need to force a reboot of your PC (either a reset button or power cycle).

The xorg log does show the resolutions and frequencies supported, so if need be we can add stuff to the xorg.conf file for the monitor section to include some of that information.

Post back with the results of trying to change resolution.

Dave :)

---

### Post by mattfurlani on 2008-10-02
> **anewguy said:**
> Okay, it's using the sis driver now.  Try looking under system/preferences/screen resolution and see if you can change your resolution to something you like better.  Be forewarned - usually the first few attempts at this aren't pretty, and you may be in a position where you will just need to force a reboot of your PC (either a reset button or power cycle).

The xorg log does show the resolutions and frequencies supported, so if need be we can add stuff to the xorg.conf file for the monitor section to include some of that information.

Post back with the results of trying to change resolution.

Dave :)

it is on 1280 x 800 res. it will let me go lower but not higher. I think this is a fairly good resolution. But i'm no expert. Did you want me to repost the log?

This is what the log says now and i'm sure its the same as before.

(--) SIS(0): Virtual size is 1280x800 (pitch 1280)
(**) SIS(0): *Default mode "1280x800" (1280x800) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)

I think my computer screen is literally not capable of anything higher than 1280 by 800. maybe that's why its having trouble with high quality 3d resolution??

anyways i gotta go to work. i hope this is what you were looking for.

---

### Post by anewguy on 2008-10-02
I could be wrong, but I *think* you are probably set up correctly now.  The log seems to indicate it is enabling 3D acceleration and everything else.

So, if you think the resolution is OK, I think we're probably done!

Please be sure to use the "Thread Tools" option at the top half of the screen and marked this thread as solved.

Good Luck!

Dave :D

---

### Post by mattfurlani on 2008-10-03
> **anewguy said:**
> I could be wrong, but I *think* you are probably set up correctly now.  The log seems to indicate it is enabling 3D acceleration and everything else.

So, if you think the resolution is OK, I think we're probably done!

Please be sure to use the "Thread Tools" option at the top half of the screen and marked this thread as solved.

Good Luck!

Dave :D

okay but if my games are still blotchy and all @#$@$##@ will i be S O L ?

---

### Post by anewguy on 2008-10-03
Depends on the game.  Is it a Linux based game, or is a Windows based game you're trying to run in Wine in Linux?  Try taking a screen shot of your problem and posting it back here (applications/accessories/take screenshot).

It also depends if the game is trying to do a lot of 3D modeling, etc., because it is quite possible the graphics chip just isn't good enough, fast enough, etc., to be able to run them.

Dave :)

---

### Post by mattfurlani on 2008-10-04
> **anewguy said:**
> Depends on the game.  Is it a Linux based game, or is a Windows based game you're trying to run in Wine in Linux?  Try taking a screen shot of your problem and posting it back here (applications/accessories/take screenshot).

It also depends if the game is trying to do a lot of 3D modeling, etc., because it is quite possible the graphics chip just isn't good enough, fast enough, etc., to be able to run them.

Dave :)

that is very much so the problem. I was thinking of discovering a dual boot with a extra XP my father acquired over damages he received from an update on his windows office computer. (phew) 

most of the linux games are blotchy (minus wormux) and don't seem like much fun. 

regardless of what I do, thank you for trying to get it set up for me.

---

### Post by bergomi on 2008-10-06
I have same problem,

Hoping 8.10 support SIS driver.

---

### Post by anewguy on 2008-10-06
Ubuntu has support for the sis driver already - just follow the advice earlier in this thread.  If you look back a little earlier in this thread you will see the Xorg.0.log and it shows it is using sis.  I believe the problems you both are having is that the sis video chip probably just isn't fast enough, have enough memory or even just doesn't support some of the video options that would allow your games to be better.

I used to have a Gateway laptop that had a unichrome pro chipset for the video, and it also just lacked things in the physical chipset to support much - as an example, there was no way to run desktop effects like compbiz (in those days it was beryl).  The chipset just plain wouldn't support it.

There are tons of things related to the video hardware that could account for some of your problems - anti-aliasing, frame rates, shading - all kinds of things.  I doubt there is any software fix to this.

Dave :)

---

### Post by ftso on 2008-10-13
I have a new installation of kubuntu 8.10 (full updated) on a new laptop with this VGA:

```
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
```

I can't use *Driver "sis"* on xorg.conf.
Now i use vesa.

I was try:

1)CTRL+ALT+F1

2)Login

3)run:
```
sudo modprobe sis
```
(no errors)
I have already installed the package:
```
xserver-xorg-video-sis
```

4)Change the word vesa to sis in option driver , on section device of xorg.conf.

5)run:
```
startx
```
Error: No screens found...

6)Change again to vesa...and run startx work perfect. 

Can somebody help me?
Is this a bug on xserver-xorg-video-sis?
:confused:

PS: I'm sorry for my bad English...:(

---

### Post by mattfurlani on 2008-10-15
> **ftso said:**
> I have a new installation of kubuntu 8.10 (full updated) on a new laptop with this VGA:

```
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
```

I can't use *Driver "sis"* on xorg.conf.
Now i use vesa.

I was try:

1)CTRL+ALT+F1

2)Login

3)run:
```
sudo modprobe sis
```
(no errors)
I have already installed the package:
```
xserver-xorg-video-sis
```

4)Change the word vesa to sis in option driver , on section device of xorg.conf.

5)run:
```
startx
```
Error: No screens found...

6)Change again to vesa...and run startx work perfect. 

Can somebody help me?
Is this a bug on xserver-xorg-video-sis?
:confused:

PS: I'm sorry for my bad English...:(
you should probably start your own thread so they can help you fix it. i've given up hope.

---

