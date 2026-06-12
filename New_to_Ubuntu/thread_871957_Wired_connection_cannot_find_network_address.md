---
title: "Wired connection cannot find network address"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by marcusesses on 2008-07-27
Hi, 

I previously posted that I was having problems with my wireless [here]("http://ubuntuforums.org/showthread.php?t=870461"). Now I seem to be having problems with a wired ethernet connection (though the problems may be related, I thought I'd start a new thread anyway).

I am currently working on an Acer Aspire 2920, with Ubuntu 8.04. As far as I'm aware, my wireless card (Intel PRO/Wireless 3945ABG) works OOTB, and I'm uncertain about wired. The OS detects all available networks (wired and wireless), but is unable to connect to any of them. 

I think it is unable to find a network address, since this is when it seems to crap out on the wired connection. 

I've listed some details below (which was a pain in the a-r-s-e, as I had to write it out on a wired computer...gross)



:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1b.0 Audio Device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI Bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI Bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2(rev 03)
00:1c.2 PCI Bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2  (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3  (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC InterfaceC ontroller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC I Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02.00.0 Ethernet Controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

:~$ lsusb

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 5986:0102 Bison
Bus 006 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

:~$ lshw -C network

*-network
    description: Ethernet interface
    product: Netlink BCM5787M Gigabit Ethernet PCI Express
    vendor: Broadcom Corporation
    physical id:0
    bus info: pci@0000:02:00.0
    logical name:eth0
    version: 02
    serial: 00:1d:72:10:7a:34
    capacity: 1Gb/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm vpd msi pciexpress bus_master cap_list ethernet      
    physical tp 10bt 10bt-fd 100bt 100bt-fd 1000br 1000bt-fd  autonegotiation
    configuration: autonegotiation=on broadcast =yes drover=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=1Gb/s
*-network
     description: Wireless interface
     product: PRO/Wireless 3945ABG Network Connection
     vendor: Intel Corporationilities
     physical id: 0
     bus info: pci@0000:04:00.0
     logical name: wmaster0
     version: 02
     serial: 00:1c:bf:00:97:e4
     width: 32 bits
     clock 33 MHz
     capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
     configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by northern lights on 2008-07-28
If you're behind a router, run ```
sudo dhclient eth0
```

Now what?

If you're wired connection still doesn't work, please also post the output of ```
ifconfig
```

---

### Post by ellgor on 2008-07-28
Hi,

Here's a tip I got, after mucking around with various settings and whatnot for months, switch the router off for a couple minutes and then restart with everything connected, the router needs to forget all previous settings and take on the new, was the explanation I got, and it WORKED, hope this helps.

Regards, Ellgor.

---

### Post by marcusesses on 2008-07-28
:~$ sudo dhclient eth0
[sudo] password for mjbaron: 
There is already a pid file /var/run/dhclient.pid with pid 7780
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1d:72:10:7a:34
Sending on   LPF/eth0/00:1d:72:10:7a:34
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Resetting the router didn't do the trick...

---

