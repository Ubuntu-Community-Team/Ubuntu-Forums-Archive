---
title: "getting started w/Intel 4965AGN"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by DavidMcA on 2008-07-09
hello! complete newbie here.  I'm trying to get a driver installed so my Intel 4965AGN wireless card will "see" my newly installed Ubuntu 7.04. There are apparently several ways to make this happen, but I'm trying the instructions at intellinuxwireless.org first.  There, I am instructed to first install a mac80211 subsystem before installing the iwlwifi driver.  The first few steps in the process went well.  However, when I try to do so, at the command "make patch_kernel", I get the following:

Kernel Makefile not found at 'lib/modules/2.6.20-15-generic/source'
If patch or script failed, check pre/ and post/ for current stage 
make: *** [compatible/modified] error 1
[B]
Any suggestions about what to do next?[/B]

Following the instructions elsewhere on the Absolute Beginner Talk forum concerning inquiries of this type, I'd like to supply the information below

1. How are you trying to get online?
wireless router
2. What hardware are you using?
Laptop Panasonic CF-T7 "Toughbook"
Dual boot with Windows XP
Intel wireless WiFi Link 4965AG
Driver Version 11.1.1.22
3. Who is your ISP? Verizon (USA)
4. Which version of Ubuntu? 7.04
5. Can you get online with any other method? Not with Ubuntu.  I must reboot on the Windows XP side.  I downloaded the software from the intellinuxwireless site to a flash drive, unplugged it, rebooted to Ubuntu, plugged the flash drive in, and downloaded the software from the flash drive to the Ubuntu desktop.
6. How are you getting online to post? Windows XP side of dual boot.
7. The commands lspca, lsusb, and lshw -C network.  See data below.
david@david-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:04.0 Signal processing controller: Intel Corporation Unknown device 2a08 (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
06:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
06:00.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
 

david@david-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:3001 Alps Electric Co., Ltd UGTZ4 Bluetooth
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0430:0501 Sun Microsystems, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
david@david-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fc300000-fc301fff irq:11
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 13
       serial: 00:0b:97:55:33:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:fc200000-fc203fff ioport:2000-20ff irq:20
8. I disabled the power management tab in the Windows network adaptor properties dialog box as advised.

---

### Post by cprofitt on 2008-07-11
If this is a new install and you are not tied to it I would reinstall 8.04 instead of 7.04. My install of 8.04 (Hardy Heron) detects my wireless card with no need for extra drivers.

---

### Post by Creap on 2008-07-12
Sorry, I missed this thread before starting a new one, only searched for "Intel 4965" and not "4965AGN", but I'm having troubles too, and I'm using 8.04. See [Intel 4965 AG or AGN not available / found]("http://ubuntuforums.org/showthread.php?t=857132").

---

