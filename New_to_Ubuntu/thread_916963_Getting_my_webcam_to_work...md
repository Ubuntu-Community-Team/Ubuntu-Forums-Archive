---
title: "Getting my webcam to work.."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-09-11
I found a source for the drivers, but I installed them to no avail. I know they work because I've installed them before on this computer (I got a new hard drive) and yet I still can't get it to work. I am willing to give whatever information you need (I'm in AP US History at the moment taking notes, so I have time), and do whatever is necessary. Thanks for the help!

---

### Post by mewithafez on 2008-09-11
Hi, I'll see what I can do, and if not there are people **much** better than me at this. First of all, what is the name of the webcam (say, Creative LifeCam blablabla)?

---

### Post by stropyboy11 on 2008-09-11
I believe it's a Ricoh something or other. It's built in to my HP DV6000T.

---

### Post by cariboo on 2008-09-11
Open up a terminal and type:

```
lspci
```

then

```
lsusb
```

Paste the output from these two commands in your next post this will help us determine what make and model of webcam you have.

Jim

---

### Post by stropyboy11 on 2008-09-11
> stropko@stropko-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
stropko@stropko-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  


Next?

---

