---
title: "Realtek Wireless Driver"
date: 2017-07-07
forum: New to Ubuntu
---

### Post by mac187 on 2017-07-07
Hi, i typed 'sudo lshw -C network'
and i got this:


*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: enp3s0f1
       version: 12
       serial: 80:fa:5b:40:bf:5f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:131 ioport:d000(size=256) memory:df314000-df314fff memory:df310000-df313fff
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 78
       serial: 00:28:f8:3e:80:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-58-generic firmware=22.391740.0 ip=10.0.0.40 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:138 memory:df200000-df201fff


the configuration line said that my driver is: iwlwifi

I just installed Ubuntu few days ago, and only driver i have updated is Nvidia, so my question is: 

I want to update to realtek driver and use the realtekdriver, (or do i have it?) and  anyone know the best solution to do it without messing anything? and is 'iwlwifi' Ubuntu's integrated driver ?

Im really new to Ubuntu so please help me ? :)

Thanx

---

### Post by CatKiller on 2017-07-07
It's showing that you have a Realtek network card using the r8169 driver and an Intel wireless device using the iwlwifi driver. If they are both working, you don't need to do anything. You do not arbitrarily "update drivers" in Linux like you might in Windows.

---

### Post by mac187 on 2017-07-07
Ok, so this shows that im using Realtek drivers and its works good?

---

### Post by CatKiller on 2017-07-07
Certainly nothing in the output you provided indicates a problem. Is it all working?

---

### Post by mac187 on 2017-07-07
Yeah, all is working on Ubuntu, but in Kali Linux, i cant see wich wireless nearby me.. Like i do in ubuntu, im using VirtualBox with Kali Linux

---

### Post by yancek on 2017-07-07
> im using VirtualBox with Kali Linux 		

Does that mean you have Kali installed in VBox?
You do know Kali has networking disabled by default?
You will likely need to use the bridged network option in VBox to see anything else.
Kali has good documentation at their site so if the problem is with Kali networking that would be a better source of information.

---

### Post by jeremy31 on 2017-07-07
If you want to control wireless from a virtual guest, you need to use a USB wifi adapter as PCI can be controlled from the host only.

As yancek stated you can use a bridge in the virtualbox install so the guest OS has internet but will usually see the connection as ethernet in the guest OS

---

### Post by QIII on 2017-07-08
Hello!

There are three question going on here:

1.  The wireless connection with the Ubuntu host, which belongs in this sub-forum.

2.  A general question about a bridged connection that belongs in the Virtualization sub-forum

3.  A question about Kali, which belongs in the Ubuntu/Debian BASED sub-forum.

Let's conclude the issue with getting wireless working in the Ubuntu host, then.  Address the other issues in their own threads.

Closed

---

