---
title: "Garbled text on boot"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by gorgor on 2013-01-07
Release 12.04 (precise) 32-bit
 Memory - 1.4 GiB
 AMD Sempron(tm) 3000+ (2 GHz)
 One 80GB HD

 description: Ethernet interface
 product: nForce2 Ethernet Controller
 vendor: NVIDIA Corporation
 physical id: 4
 bus info: pci@0000:00:04.0
 logical name: eth0
 version: a1
 serial: 00:11:2f:f2:3e:b7
 size: 100Mbit/s
 capacity: 100Mbit/s
 width: 32 bits
 clock: 66MHz
 capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
 configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.3 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
 resources: irq:22 memory:fe800000-fe800fff ioport:eff0(size=8)


Just installed 12.04 from the alt CD as the sole OS on this computer, just booted for the first time and there is what appears to be some kind of full screen terminal with a black background and white text garbled beyond recognition. I can type to it, but cant read what im typing.

---

### Post by Bashing-om on 2013-01-07
gorgor; Hi !

Likely there is no graphics driver installed.
The simplest way to install the driver is from the Additional Drivers utility. But to get to the desk top to do so, have to make a boot edit in grub's kernel boot line.

Cold boot, when bios screen clears depress and hold the shift key -> grub menu:
Press the "e" key to enter edit mode, arrow down to the line similar to this;
"linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash " arrow across and insert the term "nomodeset" -with out the quotes- before the terms "quiet splash". ctl+x to continue to boot.
See these links for details:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once you are at the desk top, left side of screen is the launcher; Choose "System Settings" -> Additional Drivers -> install the recommended driver.

Hopefully you will be good to go ![INDENT][INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

