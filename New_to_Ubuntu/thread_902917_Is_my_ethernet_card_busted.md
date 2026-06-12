---
title: "Is my ethernet card busted?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by djenge on 2008-08-27
I just installed Ubuntu 7.10 and am new to all this stuff.  Everything worked except for internet.  I'm using a different computer to search how to do it.  I connect through a router to a cable modem and I'm sure that the source is good.  I use an onboard VIA Rhine II ethernet adapter and it seems like everything installed fine, but it just doesn't connect.  When I first installed Windows, I remember it giving me issues as well, and I had to install the driver using the motherboard disk.  Here's more info that I don't understand but may help you:

       djenge@djenge-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)
00:0a.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
00:0a.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Unknown device 0015
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
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
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
djenge@djenge-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0bda:0103 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
djenge@djenge-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:30:18:c7:de:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes


Thanks

---

### Post by oilchangeguy on 2008-08-27
have you tried turning off the power to the router, and modem? do that, and also reboot the computer. if that doesn't work, can you go directly from the modem to the computer? to see if the ethernet card works in ubuntu.

---

### Post by cariboo on 2008-08-27
You could try in a terminal:

```
sudo dhclient eth0
```

Jim

---

### Post by djenge on 2008-08-27
> **oilchangeguy said:**
> have you tried turning off the power to the router, and modem? do that, and also reboot the computer. if that doesn't work, can you go directly from the modem to the computer? to see if the ethernet card works in ubuntu.

I did all of that already with no luck

---

### Post by djenge on 2008-08-27
> **cariboo907 said:**
> You could try in a terminal:

```
sudo dhclient eth0
```

Jim


It says " no DHCPOFFERS received.

No working leases in persistent database - sleeping"

---

### Post by crispy_420 on 2008-08-28
Could this be not so much a Linux issue but a router issue? Is the router not setup to assign DHCP?

---

### Post by djenge on 2008-08-28
> **crispy_420 said:**
> Could this be not so much a Linux issue but a router issue? Is the router not setup to assign DHCP?

My other desktop is connected to it and working fine.  How do I test this?

---

### Post by dRock1286 on 2008-08-28
is your other comp running windows?

---

### Post by djenge on 2008-08-28
> **dRock1286 said:**
> is your other comp running windows?


Yes

---

### Post by crispy_420 on 2008-08-29
OK we are dealing with a desktop pc right?

Lets try manually setting up the network connection. Left click the network-manager icon and select manual configuration.

Try setting up the Wired Connection, I am assuming that this option is there. With the wired connection highlighted, click properties. A new window should open. Uncheck the "enable roaming mode" option. From there you can then select DHCP as an option.

Lets see how that works out.

---

### Post by djenge on 2008-08-31
OK I finally got it working.  It was a router issue.

---

