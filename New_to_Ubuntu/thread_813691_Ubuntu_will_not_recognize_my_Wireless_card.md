---
title: "Ubuntu will not recognize my Wireless card"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Brenegars on 2008-05-31
I just got a Dell XPS 1530 with a Broadcom BCM4328 (revision 3) wireless card. I set up a dual-boot with Vista and Hardy. So far I have not been able to get ubuntu to even recognize it. I've tried several different methods that posters have recomended on the forums, and nothing has worked so far....My ethernet port works fine for the wired connection (eth0) but the wireless isn't doing anything.

This is the first time i've ever used linux, so any straightforward advice would be helpful.

This is the output from *lshw -C network*

stewart@stewart-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4f:01:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.11.6 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


Any help is greatly appreciated.

---

### Post by aysiu on 2008-05-31
You said you've tried several different methods. Can you say exactly what you've tried?

---

### Post by attari on 2008-05-31
> **Brenegars said:**
> I just got a Dell XPS 1530 with a Broadcom BCM4328 (revision 3) wireless card. I set up a dual-boot with Vista and Hardy. So far I have not been able to get ubuntu to even recognize it. I've tried several different methods that posters have recomended on the forums, and nothing has worked so far....My ethernet port works fine for the wired connection (eth0) but the wireless isn't doing anything.

This is the first time i've ever used linux, so any straightforward advice would be helpful.

Any help is greatly appreciated.


Try to Google for Ndiswrapper. I am guessing you will have to use that with WinXP drivers as no support for it in Ubuntu.

---

