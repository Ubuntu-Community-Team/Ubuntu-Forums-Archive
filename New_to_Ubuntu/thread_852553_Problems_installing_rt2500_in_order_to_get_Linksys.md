---
title: "Problems installing rt2500 in order to get Linksys wireless up and running"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by promise64 on 2008-07-07
I am as new to this as it is possible to be, so I apologize in advance for the confusing nature of this query.

I am running Ubuntu 8.04 on a Toshiba Satellite notebook computer.   My problem: I cannot get the wireless to work with my linksys WPC54GS SpeedBoost card.  After spending the better part of last night (and early morning) reading various threads looking for answers (and trying and failing to install various drivers, programs, etc.), I am at a loss.

I found one thread that seemed to be the answer (which I now can't locate).  That user mentioned the rt2500 download that comes straight from linksys and got his wireless card up and running without having to compile anything.  Per the instructions, I downloaded that and tried to install it.  When I did that I got this message:

> **Error: Dependency is not satisfiable: module assistant**
**source for rt2500 wireless network driver**

This package provides source code for the rt2500 driver for linux.  This driver supports PCI and CardBus wireless network cards with the Ralink RT2500 or RT5200 chipset.

An alternate driver, rt2500pci, is available in the rt2x00-source package and in the Linux kernel from version 2.6.24.

In order to compile the driver you need the kernel sources (or the linux-image packages from Debian).  For compile instructions look into /usr/share/doc/rt2500-source/README.Debian or simply use the module-assistant utility

Sadly, I have no idea what this all means.

Second (possibly related?) issue: When I logged in to Ubuntu, it said I needed to install a Broadcom B43 wireless driver.  When I tried to do this (from off the Ubuntu CD) the terminal displayed the following:

>  Preconfiguring packages...
Selecting previously deselected package b43-fwcutter.
(Reading database... 95658 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--12:49:29-- [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
          => 'wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-1) ...
--12:49:32-- [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
          => 'wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error status 1

??

Additionally, since I've noted other people including this information, this is what I get back when I enter "lshw -C Network," "lspci," and "iwconfig"

> ~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network 
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:79:18:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:84:27:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated  
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Again, I'm not sure what all of this means, but I thought maybe someone else might. :)

Adding to the difficulties, since the laptop is not able to get on-line at all (when I tried to plug ethernet in directly, it didn't work, though I suspect I just need to call my high speed provider and get the IP addresses--I'm used to Windows acquiring them automatically), I am having to download everything to a different computer and transfer the files via flash drive.

I appreciate any advice someone can offer.  This is my boyfriend's computer, and I was trying to help him out by fixing his crashing/slower than death system performance, but now I feel guilty because the computer can't do the one thing he really needs it to do for work.

---

### Post by promise64 on 2008-07-07
Nevermind.  Thank you; I am just going to re-install Windows on his computer (I know, I know).  But he needs this system to be functional, and I can already tell that there's no way he's going to have the patience to deal with this.

I will, however, still be installing Ubuntu on my own system, so I'll probably be back with my own questions in the near future.

---

