---
title: "Help!"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by harvey527 on 2008-11-21
I just loaded ubuntu 8.10 and my screen was only 800x600 and looked like it was in widescreen... I downloaded the updates from the update site, due to the fact that my bluetooth will not connect, why wifi will not connect and my comcast wired connection will not connect to my laptop using ubuntu... Today I turn on my computer and I have a widescreen screen of blue and I can move my mouse... anyone have any suggestions??:(

---

### Post by Vegan on 2008-11-21
Sounds like 8.10 may not like you config. I keep important stuff on a server machine that is stable and simple swing the ax and try again.

If 8.10 still fails, go back to 8.04

:guitar:

---

### Post by wahoobob on 2008-11-21
More information is needed.  What is the machine?  did you convert it entirely to Ubuntu?  Did you retain any information on it as it was installed?  Could you try to reinstall without great trouble?  I had a bad install disc burned from an iso and it gave me unusual errors.  the only fix was to burn a new install disc at the SLOWEST BURN SPEED! then check the disc by booting it and making sure the system ran correctly on the disc.  Then I installed and everything worked/updated/etc.  Let me know what you did to install and maybe that can help me or another reader give you some help.  

Best advice from your description seems to be to reinstall with a perfect bootable disc....

---

### Post by harvey527 on 2008-11-21
SONY VAIO PCG-RSOSJLK
T-Mobile MDA
Jabra BT Dongle
Belkin Wireless G Router
Arris Cable Modem

ALL Intel Hardware on the Sony

I did a full install due to the fact that I was told I had to uninstall XP PRO SP2... or else.

---

### Post by harvey527 on 2008-11-21
It is strange that it will ask my to log in and I do and then nothing happens... :confused:

---

### Post by harvey527 on 2008-11-21
Ok.. I am reloading Ubuntu 8.10 on my Sony Viao PCG-R505JLK, I am hoping this fixes everything... Any suggestions about getting the internet to work?

---

### Post by harvey527 on 2008-11-21
Nobody answered my questions from before so I go again... I just lost my job, I had to return everything, but an older laptop Sony Vaio PCG-R505JLK and they just explained that I legally have to remove their version of XP... So I am stuck here with a laptop that has a 14.5" and only 5"x7" is viewable in Ubuntu 8.10 and I can't get on the internet using my phone or my wifi or cable modem... Can someone help me out...

---

### Post by doas777 on 2008-11-21
well lets start with your ethernet/cablemodem option.

what is the output of these commands: 
```

sudo cat /etc/X11/xorg.conf

sudo lshw -c network

sudo lshw -c video

ifconfig

```

good luck man,
franklin

---

### Post by bennachie on 2008-11-21
Did you carry out a fresh install of 8.10 from a LiveCD (that is, wiping XP from the system)? Does the same problem recur if you boot Ubuntu directly from the LiveCD (that should happen if you start up the computer with the CD already in the drive)? What are the basic specifications of your laptop (CPU, RAM and hard disk size)?

---

### Post by shoot2kill on 2008-11-21
the model provided suggests the following spec... (but only has 12" screen :S )

```

Model                  PCG-R505JS/JSK/JSP PCG-R505JE/JEK/JEP PCG-R505JL/JLK/JLP PCG-R505JL/C


                       Mobile Intel® Pentium® III processor*      Mobile Intel® Pentium® III processor*
Processor
                       850 MHz&#8224;                                   750 MHz&#8224;


L2 Cache Memory        256 KB (CPU Integrated)                    128 KB (CPU Integrated)
                                                                  256 KB (CPU Integrated) for PCG-R505JLP


                       30 GB&#8225;                 20 GB&#8225;              15 GB&#8225; 40% and 60% (approximation)
Hard Disk Drive
C/D Partition          40% and 60%            40% and 60%
                       (approximation)        (approximation)


                       256 MB SDRAM**         128 MB SDRAM** (Expandable to 384 MB) 256 MB SDRAM**
Standard RAM
                       (Expandable to                                                  (Expandable to
                       384 MB)                                                         384 MB)


LCD Screen             12.1" XGA TFT

MPEG                   Available

Graphics               Intel® 815 EM Integrated Graphic

Display Cache          4 MB

Sound Capabilities     Windows® sound system compatible, 3D surround
                       Analog devices AD1881A


                       V.90/K56flex compatible modem&#8224;&#8224;
Modem


Expansion Capabilities One Type I or II PC Card with CardBus support
Connection             2 USB ports
Capabilities           Phone line (RJ-11) jack
                       i.LINK® (IEEE1394) port&#8225;&#8225;
                       Monitor (VGA) port
                       Ethernet (10BASE-T/100BASE-TX) port
                       Microphone jack
                       Headphone jack
                       Docking Station connector

```

---

### Post by LowSky on 2008-11-21
Dude you really didn't need to start a new thread, your old one seems to be about the same stuff

to type in the commands that doas777asks for plaease use terminal
its under
Applications> Accessories> terminal

---

### Post by bennachie on 2008-11-21
Your laptop may be a bit marginal for Ubuntu 8.10. The recommended minimum specifications are:

* 700 MHz x86 processor
* 384 MB of system memory (RAM)
* 8 GB of disk space
* Graphics card capable of 1024×768 resolution
* Sound card

Shortage of RAM may be the major problem, and even a maxed-out 384MB would probably be on the light side for Ubuntu. Was your Windows XP installation running at 1024×768 resolution? You could probably run Xubuntu without major problems.

---

### Post by harvey527 on 2008-11-21
I was running XP at the max resolution, not quite sure but it covered the whole screen. With screen size this small it makes it hard to do anything, because I can cannot click ok when I want to save anything in text editor. I just need to get my email, use a browser and write html, css and javascript, my MDA has a hugh memory card so, I don't really need an mp3 players. Ubuntu is not allowing me to use MAXTOR external hard drives either. I crashed the system the first time try to get wifi drivers to work.

Oh well, I just need to get a job and I can buy my own server rack again...

I am going to try to get the ethernet working using these commands..

---

### Post by doas777 on 2008-11-21
> **harvey527 said:**
> I was running XP at the max resolution, not quite sure but it covered the whole screen. With screen size this small it makes it hard to do anything, because I can cannot click ok when I want to save anything in text editor. I just need to get my email, use a browser and write html, css and javascript, my MDA has a hugh memory card so, I don't really need an mp3 players. Ubuntu is not allowing me to use MAXTOR external hard drives either. I crashed the system the first time try to get wifi drivers to work.

Oh well, I just need to get a job and I can buy my own server rack again...

I am going to try to get the ethernet working using these commands..

ok. let us knwo when you get some output. those commands will tell us whether your laptop is detecting the hardware, what it is, and how it is configured. we'll see from there.

good luck,
Franklin

---

### Post by harvey527 on 2008-11-21
sudo cat /etc/x11/xorg.conf
no such file or directory

---

### Post by doas777 on 2008-11-21
> **harvey527 said:**
> sudo cat /etc/x11/xorg.conf
no such file or directory

capitalize the 'x' in X11.

you can copy and paste in a terminal with cntrl + shift + C and cntrl + shift + V

---

### Post by harvey527 on 2008-11-21
Had to install the package from package website. Then walk downstairs and install... then plugged in cat6 and I got this..
$ sudo cat /etc/X11/xorg.conf
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
$ sudo lshw -c network
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:9
  *-network
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 03
       serial: 08:00:46:41:41:fd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:a2:8f:2c:4a:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:2e:c7:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82815 Chipset Graphics Controller (CGC)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
$ if config
> ifcofig
> 
> 
> 

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:41:41:fd  
          inet6 addr: fe80::a00:46ff:fe41:41fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:652798 (652.7 KB)  TX bytes:3204 (3.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17088 (17.0 KB)  TX bytes:17088 (17.0 KB)

Not good with writing in forums, just used to downloading the software and writing permissions to the server..

It looks like it found and test my hardware... now what?

---

### Post by doas777 on 2008-11-21
ok, it looks like you don't have a graphics driver loaded, but you do have a network card driver. 

for the network, while it is plugged in, run these commands in your terminal:

```

sudo ifdown eth0

sudo ifup eth0  

```

note that it is eth0 (last is a zero).
then run ifconfig again. heres what your looking for:
```

alpha10@21of2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2f:f5:08  
          inet addr:192.168.77.21  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2f:f508/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49741017 (49.7 MB)  TX bytes:21793538 (21.7 MB)
          Interrupt:252 Base address:0x8000 


```
notice the line "inet addr:192.168.77.21". your PC needs a simmillar line.
hopefully taking the interface down and back up will refresh your IP configuration.

are you connected to a router, or directly to the cablemodem? the cablemodel will probably not like you switching the PC that it is hooked to regularly, so power it off for 45 seconds everytime you change the device that it is attached to. boot the cablemodem first, and then the device a few seconds later.

give that a try, and mabey a reboot if you are so inclined (with it plugged into the network the whole time.)

let us knwo how it works.
franklin

---

### Post by doas777 on 2008-11-21
never mind. ignore this post

---

### Post by harvey527 on 2008-11-22
I have got my cable modem working.. Now wifi is down. Any suggestions on getting the video resolution fixed??

---

### Post by harvey527 on 2008-11-22
Intel has linux drivers for my video card any know how to open an .RPM file???

---

### Post by harvey527 on 2008-11-22
WIFI is up!!:) No videos still..:(

---

### Post by harvey527 on 2008-11-22
doas777 Thank you for helping with the internet... I did the config and did a search on my neighbors comp... he leaves upstairs... you posted something about using a windows computer and copying IPCONFIG info into eth0 manual settings and now I have ethernet and wifi... ANY ideas about the video?

---

### Post by harvey527 on 2008-11-22
Comcast and Ubuntu 8.10 two ways to get it working..

1. Plug a windows computer into ethernet cable to cable modem, go to start>run then type cmd. DOS window opens and then type ipconfig.

Get ipaddress, dns, etc and write it down.

Then plug in ubuntu computer, go to the system>administrator>users and groups>unlock then give yourself permission to do everthing.

Then right click the network icon in the top right corner of screen and edit connections. Setup connection with the ipadress, dns, etc manually entered and then click connect.

2. Plug in ubuntu computer to the ethernet cable on you cable modem, then use a pin to click the reset button on modem as soon as first light comes on, go to network icon on the computer screen (top right) and left click on auto eth0. As soon as cable modem lights up completely you should be connected..

---

### Post by doas777 on 2008-11-22
check out this thread for your video issue. it looks like what you need.
[http://ubuntuforums.org/showthread.php?p=2113867](http://ubuntuforums.org/showthread.php?p=2113867)

good luck, and let us know how it works out,
franklin

---

### Post by harvey527 on 2008-11-22
I can find a package for 915resolution. I tried installing all the intel driver packages, still not working. Not sure it I have to do something in terminal to get the packages to work... any ideas?

---

### Post by harvey527 on 2008-11-22
Sorry, I mean I can't find package 915resolution.

---

### Post by harvey527 on 2008-11-23
Ok, I just installed a program called alien (changes .rpm to .deb) and I downloaded the linux driver for the Intel 82815 video controller to my desktop, now I can't get the terminal window to find my desktop, ideas?????

---

### Post by doas777 on 2008-11-23
well, before we get into installing third party drivers, what do you get when you go to System -> Preferences -> Screen Resolution, in terms of available res and refresh settings?

Most of the time, I'm told Intel graphics drivers are built in. do you see any available drivers under System -> Administration -> Hardware drivers ?

also could you please post the contents of your xorg.0.log (go to Systems -> Administration -> System Log, and select Xorg.0.Log in the left pane). then just copy and paste teh contents. that will tell us how X detected your card/monitor.


good luck,
franklin

---

### Post by harvey527 on 2008-11-23
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 23 01:29:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82815 Chipset Graphics Controller (CGC) rev 17, Mem @ 0xf8000000/0, 0xf4000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.09  Mon Oct 27 14:37:08 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: i815M Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
(--) intel(0): Chipset: "i815"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): Kernel reported 81920 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 327676k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) intel(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) intel(0): Unable to estimate virtual size
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (hsync out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (hsync out of range)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) intel(0): Virtual size is 800x600 (pitch 1024)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01c00000 (pgoffset 7168)
(II) intel(0): Allocated of 4096 bytes for HW cursor
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c01000 (pgoffset 7169)
(II) intel(0): Allocated of 16384 bytes for ARGB HW cursor
(II) intel(0): Adding 768 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		28 128x128 slots
		6 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): DPMS enabled
(WW) intel(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event9"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event6"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Sun Nov 23 01:29:53 2008: 5139 X: client 4 rejected from local host ( uid=0 gid=0 pid=5348 )
AUDIT: Sun Nov 23 01:30:06 2008: 5139 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5352 )
AUDIT: Sun Nov 23 01:30:06 2008: 5139 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5353 )
AUDIT: Sun Nov 23 01:30:06 2008: 5139 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5354 )
(II) intel(0): Setting dot clock to 36.0 MHz [ 0x10 0x1 0x40 ] [ 18 3 4 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 36.0)
(II) intel(0): Setting dot clock to 25.2 MHz [ 0x13 0x3 0x40 ] [ 21 5 4 ]
(II) intel(0): chose watermark 0x22006000: (tab.freq 25.2)
(II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)

---

### Post by hyper_ch on 2008-11-23
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by harvey527 on 2008-11-23
Thank you... I am new to Ubuntu, I have installed it on countless tower systems for C++ developers and was told it was a great system. I am tired of Redmond and have moved to the midwest after being replaced. Again, I am not really a forum user until this week, so any help works. I printed out the information as I asked. My screen resolution options are 800x600 and 640x480 and my refresh rate options 56hz or 60hz. I hope this helpful, I am at least happy I have internet and can at least read e-mail and open webpages. I will be thrilled if I get my screen fixed and get bluetooth working, but I am sure if miracles are in my horoscope.

---

### Post by doas777 on 2008-11-23
well this chunck is shows what the problem is. I'm not sure what to do about it in intrepid however. there is the option of adding the config to your xorg.conf manually, but that will be a bit of an endeavor. it's doable though. 

```

(II) intel(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) intel(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) intel(0): Unable to estimate virtual size
(II) intel(0): Clock range: 9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (hsync out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (hsync out of range)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) intel(0): Virtual size is 800x600 (pitch 1024)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2 36.00 800 824 896 1024 600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)

```

---

### Post by doas777 on 2008-11-23
well the next step is probably to run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

in a terminal. it will launch a menu based app that will ask you questions and regen your xorg.conf file (hopefully this time with some of the specifics yours is currently lacking).

when ubuntu turned 8.10, they changed some things about where video configuration information is stored (monitor size and refresh etc), and i'm still trying to figure out where. the new way is great if it works, but what do you do when there are problems?

anyway, give dpkg-reconfigure a try and let us know.

---

### Post by diablo75 on 2008-11-23
> **doas777 said:**
> well the next step is probably to run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

in a terminal. it will launch a menu based app that will ask you questions and regen your xorg.conf file (hopefully this time with some of the specifics yours is currently lacking).

when ubuntu turned 8.10, they changed some things about where video configuration information is stored (monitor size and refresh etc), and i'm still trying to figure out where. the new way is great if it works, but what do you do when there are problems?

anyway, give dpkg-reconfigure a try and let us know.

Running this command is the very first thing I would have done if I were stuck in 800x600 (wish I had seen this thread earlier).  I would add that when it gets to the question about using the kernel buffer, answer "no".

---

### Post by doas777 on 2008-11-23
good point diablo. I'm hoping it still works, in this xorg.conf-less world.

cheers,
franklin

---

### Post by harvey527 on 2008-11-23
I give a shot and all that happened was this:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081123145007

So I went into syanptic and pulled up the package info and got a list of conflicts. Not sure if it helps, but I am doing my best.

---

### Post by doas777 on 2008-11-23
OK. I'm not sure what synaptic has to do with it, but we can deal with that in a min. did you reboot after using the dpkg-reconfigure? does your desktop fill the monitor screen now?

---

### Post by harvey527 on 2008-11-23
no change

---

### Post by doas777 on 2008-11-23
what does your xorg.conf contain now?

---

### Post by harvey527 on 2008-11-23
Here it is:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: LinuX 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 23 15:26:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82815 Chipset Graphics Controller (CGC) rev 17, Mem @ 0xf8000000/0, 0xf4000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.09  Mon Oct 27 14:37:08 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: i815M Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
(--) intel(0): Chipset: "i815"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): Kernel reported 81920 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 327676k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) intel(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) intel(0): Unable to estimate virtual size
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (hsync out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (hsync out of range)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) intel(0): Virtual size is 800x600 (pitch 1024)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01c00000 (pgoffset 7168)
(II) intel(0): Allocated of 4096 bytes for HW cursor
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c01000 (pgoffset 7169)
(II) intel(0): Allocated of 16384 bytes for ARGB HW cursor
(II) intel(0): Adding 768 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		28 128x128 slots
		6 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): DPMS enabled
(WW) intel(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event9"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event6"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Sun Nov 23 15:26:54 2008: 5142 X: client 4 rejected from local host ( uid=0 gid=0 pid=5351 )
AUDIT: Sun Nov 23 15:27:17 2008: 5142 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5355 )
AUDIT: Sun Nov 23 15:27:17 2008: 5142 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5356 )
AUDIT: Sun Nov 23 15:27:17 2008: 5142 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5357 )

---

### Post by diablo75 on 2008-11-23
Try this (it's slightly different than the previous command:

```
sudo dpkg-reconfigure xserver-xorg
```

I cut out the -phigh option... because I don't know what it's for, and I've never had to use it in the past for this reconfigure command to work.  You should have been presented with something more than a message that said your config was overwritten and a backup created.  Namely, with an interactive series of questions that (for the most part) you answer with the defaults.  So most of the time you'd just be pressing the Enter key.

(Here's what the -phigh option is for:  [http://ubuntuforums.org/archive/index.php/t-346138.html](http://ubuntuforums.org/archive/index.php/t-346138.html))

---

### Post by harvey527 on 2008-11-23
Not sure what this is supposed to do. It just keeps trying to detect my keyboard whether I say yes or no and then it just goes a page of what is supposed to find and does nothing.

---

### Post by doas777 on 2008-11-23
so, are you able to complete dpkg-reconfigure ? I would let it configure the keyboard, and enter the keys it asks for. does it crash or something?

the dpgk-reconfigure command will cause xserver to query the hardware and the user for the information needed to create a new xorg.conf file. the xorg.conf traditionally holds much of your hardware configuration. the one you posted on the first page is almost empty, and does not contain specs for your vid card or your monitor. we're hoping that this information will be filled in by reconfiguring xserver.xorg

---

### Post by harvey527 on 2008-11-23
Ok, I made it through and all it does is let me set my keyboard to pc104, I rebooted and get the same. I suppose I am doomed to extreme head aches and not being able to save the code that I write, but I least I can got 400 emails telling me I overqualified (pretty sad that I am overqualified to deliver papers or wear a paper hat and flip burgers, even too overqualified to ring bells).

---

### Post by harvey527 on 2008-11-23
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux harvey527-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 23 16:43:34 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82815 Chipset Graphics Controller (CGC) rev 17, Mem @ 0xf8000000/0, 0xf4000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.09  Mon Oct 27 14:37:08 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: i815M Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
(--) intel(0): Chipset: "i815"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): Kernel reported 81920 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 327676k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) intel(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) intel(0): Unable to estimate virtual size
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (hsync out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (hsync out of range)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) intel(0): Virtual size is 800x600 (pitch 1024)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01c00000 (pgoffset 7168)
(II) intel(0): Allocated of 4096 bytes for HW cursor
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c01000 (pgoffset 7169)
(II) intel(0): Allocated of 16384 bytes for ARGB HW cursor
(II) intel(0): Adding 768 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		28 128x128 slots
		6 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): DPMS enabled
(WW) intel(0): Direct rendering disabled
(WW) intel(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event9"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event6"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Sun Nov 23 16:43:48 2008: 5137 X: client 4 rejected from local host ( uid=0 gid=0 pid=5346 )
AUDIT: Sun Nov 23 16:44:00 2008: 5137 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5350 )
AUDIT: Sun Nov 23 16:44:00 2008: 5137 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5351 )
AUDIT: Sun Nov 23 16:44:00 2008: 5137 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5352 )

---

### Post by doas777 on 2008-11-23
who do you get from:
```
sudo apt-get install xserver-xorg-video-intel --reinstall
```

---

### Post by harvey527 on 2008-11-23
~$ sudo apt-get install xserver-xorg-video-intel --reinstall
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of xserver-xorg-video-intel is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
laptop:~$

---

### Post by harvey527 on 2008-11-23
package manager says xserver-xorg-video-intel is obsolete.

---

### Post by doas777 on 2008-11-23
ok, can you tell which driver you do have installed?

---

### Post by harvey527 on 2008-11-23
That's strange it says I am using xserver-xorg-video-intel, but I have a ton of over packeges for other video cards installed as well.

---

### Post by doas777 on 2008-11-23
well some of the other packages are probably the stock oss drivers used in low video mode. they are prolly there just in case. 

I guess at this point, you may have to manually configure your xorg.conf.
unfourtunatly i have'nt used an intel card in years, so i can't be of too much help.

this [doc]("https://wiki.ubuntu.com/X/Config/Resolution") will get you started with how the xorg is structured, and some googleing ought to help you get the intel specific parts filled in. at a minimum you will need to define a monitor with vrefresh and hsynch appropriate for your laptop screen, and add a driver and busid for your device. [this]("http://www.funnestra.org/ubuntu/intrepid/") may also be of help (scroll all the way down to "fix Screen Resolution")

good luck man,
franklin

---

### Post by harvey527 on 2008-11-23
I tried ADDMode and it keeps saying that output does not exist.

---

### Post by harvey527 on 2008-11-23
ok.. I am having issues and get errors with addmode because it appears I have nothing set for the video type and newmode just gives me tons of errors. The instructions for newmode has a dead link. Anyone have instructions for newmode??

---

### Post by harvey527 on 2008-11-23
This might help...

[https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045896.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045896.html)

---

### Post by harvey527 on 2008-11-23
Anyone know of a good BASH tutorial for this type of thing?

---

### Post by harvey527 on 2008-11-24
I tried some I found on a forum:
```
~$ xrandr --newmode "640x480_60.00"  23.86  640 656 720 800  480 481   484 497  -HSync +Vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  152 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
~$ xrandr --newmode "1024x768_60.00" 23.86  640 656 720 800  480 481  484 497  -HSync +VSYNC
harvey527@harvey527-laptop:~$ Xrandr --addmode  VGA-0  1024x768_60.00 
bash: Xrandr: command not found
~$ xrandr --addmode  VGA-0  1024x768_60.00
xrandr: cannot find output "VGA-0"
~$ xrandr --addmode VGA 1024x768_60.00
xrandr: cannot find output "VGA"
~$ xrandr --addmode S-video 1024x768_1023_60.00
xrandr: cannot find output "S-video"

```

---

### Post by harvey527 on 2008-11-24
I posted my question on other linux forums and got no reply. I was wondering maybe I should remove the 8.10 driver and try the 8.04 driver. I was also thinking about getting 8.04, but my CDR is not working, what do I do? Can I get 8.04 and then upgrade to 8.10 without losing my screen resolution. Will 8.04 fix my problem? Will another linux distro fix my problem?:confused:

---

### Post by harvey527 on 2008-11-24
I would like to thank doas777 for helping me.

---

### Post by harvey527 on 2008-11-24
Can anyone direct me to a forum that might be able to help me with this issue??

---

### Post by harvey527 on 2008-11-24
Anyone know why the HARDY update pages aren't working on packages.ubuntu.com???

---

### Post by doas777 on 2008-11-24
> **harvey527 said:**
> I would like to thank doas777 for helping me.

any time man. I wish i could have been of more help.

goos luck and have fun,
franklin

---

### Post by harvey527 on 2008-11-24
$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by crjackson on 2008-11-24
There is a big difference under the hood between Hardy and Intrepid. I too have poor video on Intrepid using an older laptop. Hardy however runs awesome on that system. I would suggest you try Hardy or even a different distro better suited to older hardware.

---

### Post by harvey527 on 2008-11-24
I have an older laptop and my only OS is Ubuntu 8.10, if I switched to Hardy, how would I do it without a CDR?? Is the software included different?? Would I be able upgrade and keep the video settings?? I have some drivers I haven't tried, but the are tar.gz files. Any ideas??

---

### Post by harvey527 on 2008-11-26
I get a feeling this issue is not resolvable, I think there is a big issue with Ubuntu and Intel drivers. I have read a bunch of treads with the same driver and not one of them have been resolved. I think that the people who wrote them just gave up.

---

### Post by harvey527 on 2008-11-26
I tried adding a FOO and getting errors:
```
Section "Device"
    Identifier "My Graphic Board"
    ...
    Option "Monitor-LVDS" "Internal Panel"
    Option "Monitor-VGA" "External VGA Monitor"
  EndSection
  Section "Monitor"
    Identifier "Internal Panel"
    ...
  EndSection
  Section "Monitor"
    Identifier "External VGA Monitor"
    ...
  EndSection

```

Anyone have any ideas.

I am also getting an error trying to add modeline:

```
Modeline "1024x768_60.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
    Option "PreferredMode" "1024x768_60.00"

```

Any got any ideas??

---

### Post by harvey527 on 2008-11-26
I read something about how to write driver for linux and 82815, but I can get the screen to show the screen to install the compiler. Anyone have any ideas for a compiler that I could use??

---

### Post by harvey527 on 2008-11-26
Again I think this is not an issue that can be resolved using ubuntu. I tried to create a driver and can't get text editor or compiler screens to allow me to save or install. I am also getting the feeling that nobody in the Ubuntu forums as the ability to fix this either. I guess this is one issue that can only be fixed by another distro of linux anyone have any ideas??

---

### Post by harvey527 on 2008-11-26
According to wikipedia the DDC can be disabled in linux by using
```
Option "NoDDCValue"

```
Since the DDC is not going recognize INTEL how can enter this command???

---

