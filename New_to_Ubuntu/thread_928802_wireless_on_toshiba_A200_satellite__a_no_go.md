---
title: "wireless on toshiba A200 satellite  a no go"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by gopher66ca on 2008-09-24
Hi all,

Computer literate but new to Ubuntu 8.04.1 and a bit overwhelmed, hope some of the old hands may offer guidance or a lead to persue.

Laptop is dual boot, Vista original installed, Toshiba satellite A200.  wired connection works out of box, wireless does not.  Wireless card is Intel Pro Wireless 4965 AG.  Have followed troubleshooting on site as best i can, and am going through some of the linux manuals online now, but this has me stumped after 4 days trying.

result of lshw -C network are:

david@davidmobiledaca:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:15:71:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.12 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

from this can i assume that Ubuntu recognized presence of the wireless card....now what next?

btw have tried to use windows driver via ndiswrapper which indicated installed driver but nothing beyond that.  then i realized from reading a native driver should work..

also, in system/administration/network...only my wired connection is shown..no indication that the wireless is there at all.

any leads i can persue, have already searched and attempted via the forums here without result..?

appreciated all.

---

### Post by gopher66ca on 2008-09-25
nothing,?

day five now, back to vista

---

