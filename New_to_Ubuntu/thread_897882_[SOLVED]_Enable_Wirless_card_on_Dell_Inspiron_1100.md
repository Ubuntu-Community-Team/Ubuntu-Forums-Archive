---
title: "[SOLVED] Enable Wirless card on Dell Inspiron 1100;  using Ubuntu 8.04"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by robdessoy on 2008-08-22
Hello, I'm very new to this operating system (I have only every used Windows and fed up with my laptop running so slow).I have installed Ubuntu 8.04(very easy) and been trying for 2 night to get my wireless card working (get the light on) and connect to the internet, with no success. However, I can connect when I plug in my Ethernet cable. I think it is something to do with my wirless interface being DISABLED. I have added some info below that the terminal session returns when I type "sudo lshw -C network". Further down this post I have shown the results of the command lspci. Any help or guidance would much appreciated.

robdessoy@robdessoy-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:e9:da:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.2 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:c6:2d:79:f3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


When I run lspci I get the following

robdessoy@robdessoy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by youthforlinux on 2008-08-22
I found this:

[http://sidulus.textdrive.com/bcmwl5sys.zip]("http://sidulus.textdrive.com/bcmwl5sys.zip")

thats the driver and use this command after extracting the driver

run this:

```
sudo bcm43xx-fwcutter -w /lib/firmware (enter the path to the bcmwl5.sys file here)
```


Oh and you might have to install the bcm43xx-fwcutter

---

### Post by robdessoy on 2008-08-24
Thanks for your help. With the info you gave me it seems to fit into place. I ended up reinstalling the Operating system and then downloaded the drivers and install them. It took me a while to figure out which drive (legacy or not) and it workd.

I'm connected to my wireless network now.

Many thanks for your help, much appreciated.

---

### Post by youthforlinux on 2008-08-24
good to know :)

enjoy ubuntu!!!!

---

