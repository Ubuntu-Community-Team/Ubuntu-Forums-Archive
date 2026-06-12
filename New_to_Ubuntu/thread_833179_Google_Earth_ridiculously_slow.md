---
title: "Google Earth ridiculously slow"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-18
I have two partitions on my machine. One has Windows Vista Home Premium, and the other has Ubuntu (8.0.4).

When I boot into Vista, Google Earth works well.

I've just installed Google Earth on Ubuntu, because I'm wanting to move all my programs over to Ubuntu.

However, Google Earth runs so slow on Ubuntu that it's unusable. (Each frame takes about a second to refresh, so it takes a couple of minutes to do what takes a couple of seconds on Vista.)

As Vista and Ubuntu are on the same machine, and Google Earth works well on Vista, it's obviously not because the hardware is too slow.

What can I do to fix this problem and get Google Earth to run as fast on Ubuntu as on Vista?

---

### Post by cmnorton on 2008-06-18
There are several places to start to diagnose this.

1) Look through /var/log/messages /var/log/syslog, and /var/log/kern.log

2) Use ps and top to see what's running?

3) What are your graphics set to? You might have to look in /etc/X11/xorg.conf to see or use the settings in System -> Administration.

4) What is the browser type, and have you tried installing and using another?

---

### Post by Paddy Landau on 2008-06-18
Thanks for the suggestions.

Unfortunately, the entries in /var/log/messages, syslog and kern.log are gobbledegook to me.

I also don't know what to look for when I run ps and top.

> **cmnorton said:**
> What are your graphics set to? You might have to look in /etc/X11/xorg.conf to see or use the settings in System -> Administration.
Again, I don't know what to look for. How do I know what my graphics are set to?

I had tried to set up the dual monitors as described in [another post]("http://ubuntuforums.org/showthread.php?t=221174"), but failed, and so I reverted to the initial set-up.

If you can give me some idea of what to look for, I'd really appreciate it.

---

### Post by wolfen69 on 2008-06-18
google earth requires you to use the proper video drivers to run correctly.

---

### Post by Paddy Landau on 2008-06-18
> **wolfen69 said:**
> google earth requires you to use the proper video drivers to run correctly.
Thanks for that. How do I tell what video drivers I need for my screens, then? I'm new at Ubuntu, so I'm swimming (drowning) in the dark!

---

### Post by nikolaos on 2008-06-30
Just disable the Atmosphere Option from the View menu. This will speed up things a bit. I think it is a bug though. Maybe downloading a previews version will work better.

---

### Post by wolfen69 on 2008-06-30
go to system>admin>hardware drivers and install.

---

### Post by billgoldberg on 2008-06-30
> **cmnorton said:**
> There are several places to start to diagnose this.

1) Look through /var/log/messages /var/log/syslog, and /var/log/kern.log

2) Use ps and top to see what's running?

3) What are your graphics set to? You might have to look in /etc/X11/xorg.conf to see or use the settings in System -> Administration.

4) What is the browser type, and have you tried installing and using another?

This kind of answer is totally useless in the absolute beginners forum.

-- 

With reading the thread, I can suggest this:

1. Make sure the graphics card drivers are installed (system -> administration -> hardware drivers)

2. Turn of compiz fusion, when using google earth (download the compiz fusion icon (applications -> add/remove))

---

### Post by Paddy Landau on 2008-07-01
Thanks for all the answers.

I've taken the easy way of disabling the atmosphere. It seems (from other posts and lots of experimentation) that:

[LIST=1]
[*]There may be a bug, though I'm unsure where.
[*]Linux doesn't handle my screen hardware quite as well as Windows does.
[/LIST]

---

### Post by philinux on 2008-07-01
Open a terminal window. Accessories Terminal and type 

lspci 

That's a lower case L at the beginning.

Copy and paste the output back here.

---

### Post by Paddy Landau on 2008-07-01
> **philinux said:**
> lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
Hope that helps.

---

### Post by philinux on 2008-07-01
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

That's your graphics driver.

What shows under system >Admin>Hardware drivers

---

### Post by Paddy Landau on 2008-07-01
Thanks for the info.

---

### Post by Paddy Landau on 2008-07-01
> **philinux said:**
> What shows under system >Admin>Hardware drivers
Nothing at all! An empty window. "No proprietary drivers are in use on this system."

---

### Post by philinux on 2008-07-01
According to synaptic your drivers are installed by default.
x-server-xorg-video-intel -- Intel i8xx, i9xx display driver 

as it's installed on my system .


Run glxgears in the terminal and see what frame rate you get.

---

### Post by Paddy Landau on 2008-07-01
> **philinux said:**
> Run glxgears in the terminal and see what frame rate you get.
```
4684 frames in 5.0 seconds = 936.731 FPS
4733 frames in 5.0 seconds = 946.468 FPS
4716 frames in 5.0 seconds = 943.059 FPS
4745 frames in 5.0 seconds = 948.851 FPS
4757 frames in 5.0 seconds = 951.334 FPS
4722 frames in 5.0 seconds = 944.357 FPS
4699 frames in 5.0 seconds = 939.747 FPS
4806 frames in 5.0 seconds = 961.076 FPS
4789 frames in 5.0 seconds = 957.736 FPS
```And so on.

---

### Post by thavid on 2008-07-13
I, when using Gutsy with the proprietary intel driver, got Google Earth running very well. Since using Hardy, it's really unusable (is it because it's not using the intel's proprietary driver)? Here goes my lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
**00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)**
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Is there a way to force the system to use intel's driver? I looked at xorg.conf, but since Hardy, the dev's have made big changes in Xorg and therefor, there is no more Device section for the grafic card...

---

### Post by oscarmeyer51 on 2008-07-14
I also turned off atmosphere in Google Earth 4.3 to get 'reasonable' response (Select View from the toolbar menu and deselect Atmosphere). I still get choppy redraws when going to options or other toolbar selections.

My glxgears result follow:

3689 frames in 5.0 seconds = 737.776 FPS
3820 frames in 5.0 seconds = 763.885 FPS
3786 frames in 5.0 seconds = 757.097 FPS
3811 frames in 5.0 seconds = 762.050 FPS
3772 frames in 5.0 seconds = 754.388 FPS
3810 frames in 5.0 seconds = 761.941 FPS
3808 frames in 5.0 seconds = 761.472 FPS
3785 frames in 5.0 seconds = 756.996 FPS

Lastly, I also get nothing in the hardware drivers. I get this output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
05:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
05:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
05:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
05:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
05:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
05:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
05:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by Retro Gamer on 2008-07-14
..Before I found this one I was going to make a new post on this very subject & sorry to hear I'm not the only one with the problem in the latest Ubuntu.

     ..I am running Ubuntu 8.04.1 on my Acer Aspire 3680 with an Intel Celeron M CPU 430 @ 1.73GHz, 2gigs of sheep and running the Intel 945G integrated graphics controller. I have the 3d desktop effects on and all that jazz... Direct rendering is on as well, but some 3d apps are very sluggish most noticeably being Google Earth. I run Quake, Quake2, Quake3, Half-life, etc etc quite well(not as good as in XP) in Linux so it seems odd that Google Earth would run so sluggish in Linux compared to quite speedy in XP. Is it bad programming on the part Google's Linux port of the app? My xorg.conf is pretty basic and the only line I changed was: (Identifier	"Intel Corporation 82801G")
 from: (Configured Video) to reflect my chip set...

============================================================

# xorg.conf (X.Org X Window System server configuration file)

#

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

	Identifier	"Intel Corporation 82801G"

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

=========================================================

sudo lshw -C Video yielded this:

  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


     ..It might not bother me as much if I didn't know it seemed to run quite well in Ubuntu 7.10 and now it doesn't. If anyone has any ideas or changes I might make please let me know... TIA

---

### Post by SuperSlickNick2000 on 2008-10-16
Hi I am also running hardy and essentially have the same video card as you (I have a sony vaio) anyway you may want to try this:

Open Terminal (Applications -> Accessories -> Terminal) and type:
export LIBGL_ALWAYS_INDIRECT=true
googleearth

I found this fix at:
[http://ubuntuforums.org/archive/index.php/t-552178.html](http://ubuntuforums.org/archive/index.php/t-552178.html)

It worked for me

---

### Post by nisidabay on 2008-10-25
Hi:
Currently I'm using the last release of Linux Mint that comes with FluxBox. I got a Sony Vaio Laptop with 1 Gb ram. It's not a state of the art computer but runs well.
I installed the last version of Google Earth, 4.3  and had the same problems. 
Without touching anything of the configurations files what I did was installing an older version and now it runs smoother and faster.

Steps:
1)From an xterm:
apt-get update
apt-cache search googleearth
-----
This is what I got:
googleearth - meta package for Google Earth!
googleearth-4.2 - Google Earth! 4.2 - binary files
googleearth-4.2-data - Google Earth! 4.2 - data files
googleearth-4.3 - Google Earth! 4.3 - binary files
googleearth-4.3-data - Google Earth! 4.3 - data files
-----
I chose googleearth-4.2 - Google Earth! 4.2 - binary files and installed it by:

2)apt-get install googleearth-4.2

Once everything went ok now Google is telling me that it's a newer version available, which of course I'm not going to install.

Hope it helps.

---

### Post by SunnyRabbiera on 2008-10-25
well google earth under linux runs under WINE so no wonder you are having issues, thats why i dont use google earth.

---

### Post by rzrgenesys187 on 2008-10-25
> **nikolaos said:**
> Just disable the Atmosphere Option from the View menu. This will speed up things a bit. I think it is a bug though. Maybe downloading a previews version will work better.

Awesome worked great for me.

---

### Post by treesurf on 2008-10-25
It's still a bit choppy, but unchecking the Atmosphere option sped things up tremendously and has made the program usable again.  Thanks.

---

### Post by the8thstar on 2008-10-26
> **SunnyRabbiera said:**
> well google earth under linux runs under WINE so no wonder you are having issues, thats why i dont use google earth.


??? Er, what?

---

### Post by Paddy Landau on 2008-10-27
> **SunnyRabbiera said:**
> well google earth under linux runs under WINE so no wonder you are having issues, thats why i dont use google earth.
I don't know whether it runs under WINE, but why would you want to?

Just run the normal Google Earth for Linux!

---

### Post by swaprava on 2009-12-17
> **philinux said:**
> Open a terminal window. Accessories Terminal and type 

lspci 

That's a lower case L at the beginning.

Copy and paste the output back here.

Hi, I'm also using ubuntu  8.04 and having similar symptoms, hence can provide the input:

```
 lspci 
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

moreover, I tried compiz fusion, ubuntu crashes immediately ...

---

### Post by wujastyk on 2010-04-16
> **nikolaos said:**
> Just disable the Atmosphere Option from the View menu. This will speed up things a bit. I think it is a bug though. Maybe downloading a previews version will work better.
Disabling the Atmosphere worked very well for me too.  I've been struggling with this for some time, fiddling with xorg.conf, diagnosing my graphics card, and whatnot.  But disabling the atmosphere has moved Google Earth from "Unusable" to "Usable" for me.

Thanks!

Dominik

---

