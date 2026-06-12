---
title: "Can't figure out Wireless Support"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by TJTorola on 2008-06-13
Hey all, I'm brand new to Ubuntu and Linux and I need help setting up my Wireless connection to my laptop. I'm using a Dell Inspiron 1525 with hardy heron. I've looked at the guides and tried my best to follow them but always end up getting lost. Can someone help point me in the right direction. Please and thank you :)

---

### Post by wolfen69 on 2008-06-13
go to system>admin>hardware drivers. see if there is a driver for it. if there is, then you can click the network icon on the taskbar and enter the appropriate info.

---

### Post by ukripper on 2008-06-13
> **TJTorola said:**
> Hey all, I'm brand new to Ubuntu and Linux and I need help setting up my Wireless connection to my laptop. I'm using a Dell Inspiron 1525 with hardy heron. I've looked at the guides and tried my best to follow them but always end up getting lost. Can someone help point me in the right direction. Please and thank you :)

can you post output of the following command :
in terminal type:
```
lshw -C network
```

and then type
```
iwconfig
```

---

### Post by Ub1476 on 2008-06-13
Post the output of this in the terminal:

```
lspci
```

That will show your wireless card. Sometimes, you just need to install drivers from System>Administration>Hardware Drivers, but if there's no Linux driver available, you need to use [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by TJTorola on 2008-06-13
Its not listing anything in there

---

### Post by Hospadar on 2008-06-13
Here's a post from someone who looks like they've gotten it to work:
[http://ge.ubuntuforums.com/showthread.php?t=740080](http://ge.ubuntuforums.com/showthread.php?t=740080)

---

### Post by TJTorola on 2008-06-13
> can you post output of the following command :
in terminal type:

```
lshw -C network
```

and then type

```
iwconfig
```

> Post the output of this in the terminal:

```
lspci
```

That will show your wireless card. Sometimes, you just need to install drivers from System>Administration>Hardware Drivers, but if there's no Linux driver available, you need to use ndiswrapper.

This is what I got when I put those three commands into the terminal.

```
tjtorola@tjtorola-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:48:5b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
tjtorola@tjtorola-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tjtorola@tjtorola-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
tjtorola@tjtorola-laptop:~$ 

```

When I go into System>Administration>Hardware Drivers it doesn't list anything for me. Does this mean I need to install ndiswrapper?

---

