---
title: "no wireless on laptop - including codes"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by sp00k- on 2008-07-25
I have a Toshiba Satellite A205-S5843, 2.5 x32, 2g SDRAM, 160GB HD.  I have no other OS installed on the system.  The system is brand new and every thing worked fine (except for constant crashes related to windows explorer) for the 3 weeks I had Vista.  I deleted Vista with a KillDisk bootdisk and everything in ubuntu is working magnificently except for wireless.  Thanks for reading.

CODE: lspci

OUTPUT:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
____________________________________________________________________

CODE:  lsusb

OUTPUT:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
_____________________________________________________________________

CODE: lshw -C network

OUTPUT:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:36:bb:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.11.5 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by bobnutfield on 2008-07-25
I believe that the Atheros chipset needs madwifi. This thread should help:

[http://ubuntuforums.org/showthread.php?t=868066&highlight=Atheros+wireless]("http://ubuntuforums.org/showthread.php?t=868066&highlight=Atheros+wireless")

Bob

---

### Post by sp00k- on 2008-07-25
thanks Bob.  I downloaded it but it didn't work.  I will read that thread.

---

### Post by sp00k- on 2008-07-25
OK, I AM BACK.

I read the thread and did every thing detailed in all 7 pages, even if I had already done them in the last few days. Unfortunately it got me no where. I already have madwifi. When I click on the networking icon in the upper right hand corner, I get "Connect to 802.1x........." But I see no networks to connect to when I right click and go to "edit wireless networks". I see the control panel, but no networks are detected. Any ideas? Thanks so much for your time, folks. I really appreciate it.

---

### Post by bobnutfield on 2008-07-25
I have never used madwifi, so I do not know if manually setting up your wireless would work the same, but your might try to manually set it up with the following commands:

> sudo iwconfig #with no arguments to find out what your wireless is known as by Ubuntu (might be wlan0 or ath0)

> sudo iwconfig mode managed
> sudo iwconfig enc ************ #if you use encryption, it goes here
> sudo iwconfig ath0 essid <your network name> #the name of the network you are trying to connect to
> sudo dhcpcd ath0
 #you use this if you are using dhcp instead of a static IP
> sudo ifconfig ath0 up #if you can see lights on your wireless, they should light at this point.

You might also try:

> sudo iwconfig ath0 scan

#this will scan all the networks within range.

This is th method I use to set up my wireless, but, as I mentioned I do not use madwifi but it works fine for me with ndiswrapper.  If these commnads do bring up your wireless, you might need to place them in in etc/rc.d/rc.d.local so that it comes up at boot.  This method has worked for me with Ubuntu, Slackware and Fedora.  It's worth a try, and hopefully someone else will chime in with some suggestions if this does not work for you.

Bob

---

