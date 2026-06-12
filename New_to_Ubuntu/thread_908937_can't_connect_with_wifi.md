---
title: "can't connect with wifi"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by samuelj on 2008-09-03
my connection is ADSL through a motorola modem/belkin N router. 

hardware is acer aspire 5720z
windows vista was the original OS

ISP is att.net in the US

Ubuntu version is 8.04

if i use the hard wire, i'm great. if not, there is no wifi. 

i am connected through the hardwire to get online access at the moment. 

lspci output

samuelj@samuelj-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
samuelj@samuelj-mobile:~$ 


lsusb output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

samuelj@samuelj-mobile:~$ lsusb
Bus 007 Device 002: ID 5986:0102 Bison 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 413c:3016 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
samuelj@samuelj-mobile:~$ 

lshw -class network output

samuelj@samuelj-mobile:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:55:67:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 ip=192.168.2.3 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


i do not dual boot to windows. 



another issue that has arisen, my touchpad no longer works. i have had to start using a wired mouse. no clue as to why though. didn't have problems before. i have wiped the drive and reinstalled ubuntu with no luck on that part.

---

### Post by nvikram on 2008-09-03
> **samuelj said:**
> my connection is ADSL through a motorola modem/belkin N router. 

hardware is acer aspire 5720z
windows vista was the original OS

ISP is att.net in the US

Ubuntu version is 8.04

if i use the hard wire, i'm great. if not, there is no wifi. 

i am connected through the hardwire to get online access at the moment. 

lspci output

samuelj@samuelj-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
samuelj@samuelj-mobile:~$ 


lsusb output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

samuelj@samuelj-mobile:~$ lsusb
Bus 007 Device 002: ID 5986:0102 Bison 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 413c:3016 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
samuelj@samuelj-mobile:~$ 

lshw -class network output

samuelj@samuelj-mobile:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:55:67:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 ip=192.168.2.3 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


i do not dual boot to windows. 



another issue that has arisen, my touchpad no longer works. i have had to start using a wired mouse. no clue as to why though. didn't have problems before. i have wiped the drive and reinstalled ubuntu with no luck on that part.

Hmmm... for the wifi, you may want to try ndiswrapper, you can find instructions here. [http://theubuntublog.wordpress.com/2007/04/08/ndiswrapper-update/](http://theubuntublog.wordpress.com/2007/04/08/ndiswrapper-update/) But for this you will need your wireless card driver so find that out, download the .inf and in Step 10, insert your .inf file their.

---

### Post by samuelj on 2008-09-03
the driver should be the ath5k. (i have went back and forth between that and madwifi with zero luck. if i am incorrect, please tell me how to get that info. i am a new user who is switching one system to linux. 
(baby steps)

my knowledge of linux is very very limited

---

### Post by Crafty Kisses on 2008-09-03
How about this output> iwconfig

---

### Post by samuelj on 2008-09-03
when i do the ndiswrapper update, the only results i get are 
ndisgtk
ndiswrapper-common
ndiswrapper-utils 1.9

that's it. is this an issue?

---

### Post by samuelj on 2008-09-03
samuelj@samuelj-mobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

samuelj@samuelj-mobile:~$

---

