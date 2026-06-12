---
title: "Broadcom Wifi Issues"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by joum on 2012-02-14
Greetings all!

I have a Samsung SF310 laptop with a Broadcom wireless adapter.

It has worked properly with my home wireless network, but now my home network does not show up in network manager.

I can see other networks and the same computer can connect to the said network in the windows partition.

I tried both STA and original ubuntu drivers with no success, NDISWRAPPER: no success.

Also tried manually adding the network as hidden, still, no success.

I'm posting in advance the LSPCI output, if someone needs any other info, please let me know.

Th ndiswrapper support wiki does not list my PCI card as compatible with the program. Tried with the available drivers in Samsung's site to the Windows XP version. Nothing changed.

Any help would be most welcome as i'm trying to ditch windows for good but cant get this working for days now... :(

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 3D controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by openation1 on 2012-02-14
WELL I HOPE THIS HELPS YOU... 
this worked for me.... gotta do this. one line at a time.,..

open your terminal and paste this..

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmw1-kernel-source
sudo reboot

after that you reboot your computer and it should be there. good luck...

---

### Post by openation1 on 2012-02-14
hello? tell me if this was helpful to you....:D

---

### Post by lkraemer on 2012-02-16
joum,
If you installed ndiswrapper, and also are trying the Default Ubuntu Driver there will be conflicts.  You MUST pick one method, stick to it.  I'd suggest removing the Windows drivers and ndiswrapper.

Have a look here for a method to remove the Windows Drivers and ndiswrapper.  The HOWTO: is out of date, but all you are needing is the method.  Just substitute the current Ubuntu driver's name where you see B43 in the HOWTO:

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

openation1's method is certainly another method to get the Broadcom Firmware for your Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01).


lk

---

