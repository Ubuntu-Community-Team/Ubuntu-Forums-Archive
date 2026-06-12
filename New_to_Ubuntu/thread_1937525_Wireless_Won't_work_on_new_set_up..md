---
title: "Wireless Won't work on new set up."
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Bikeguy41 on 2012-03-08
I am sure this is/has been covered somewhere in the forum. Though I am computer literate, Linux, and now Ubuntu are brand new to me. Several months ago I bought a book with 10.4 on the CD, installed in on my desktop, loved the interface, but could never get the HP desktop to find the wireless connection. So, I just ignored it. Then I bought this super Lenovo Thinkpad and thought, why not install Ubuntu on it as well. Everything went well, but I have no wireless connection. I can connect it through the ethernet, and it works.
I installed 11.10. So, can someone start me in the right direction? My laptop is useless without wireless. 
Thanks, from a very brand new member of the forum.

---

### Post by jerome1232 on 2012-03-08
first have you checked the additional drivers tool? Some propertery drivers can't be included in the kernel so check that first. Temporarily connect the laptop with a Ethernet cord and

Click the Gear icon top right, system settings, additional drivers, if it finds any install them.

Failing that let's figure out what card you have can you post the output of this command, please for readability wrap the output in code tags, click go advanced, highlight all output you pasted in, and click the # symbol.

```
sudo lshw -C network
```

---

### Post by Bikeguy41 on 2012-03-08
> **jerome1232 said:**
> first have you checked the additional drivers tool? Some propertery drivers can't be included in the kernel so check that first. Temporarily connect the laptop with a Ethernet cord and

Click the Gear icon top right, system settings, additional drivers, if it finds any install them.

Failing that let's figure out what card you have can you post the output of this command, please for readability wrap the output in code tags, click go advanced, highlight all output you pasted in, and click the # symbol.

```
sudo lshw -C network
```

Okay, when I clicked the additional drivers, nothing happened. Did download a lot of updates.
In Terminal:Here is what I got.
[code]  *-network DISABLED      
       description: Wireless interface 
       product: Centrino Wireless-N + WiMAX 6150 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 67 
       serial: 40:25:c2:58:ed:74 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-16-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:43 memory:d0500000-d0501fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 06 
       serial: f0:de:f1:8a:34:b8 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=67.165.250.137 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s 
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d #

---

### Post by jerome1232 on 2012-03-08
hmmm, it looks like it's recognized and has a driver installed, is there a physical switch somewhere on the laptop you can push to turn the wifi on or off? I understand that if lshw says it's DISABLED then that means it's simply turned off via a hardware switch.

---

### Post by Bikeguy41 on 2012-03-09
That's what I thought, but the switch was on. 
Thanks

---

### Post by idoitprone on 2012-03-09
wifi software blocked?


sudo rfkill list

[http://linuxwireless.org/en/users/Documentation/rfkill](http://linuxwireless.org/en/users/Documentation/rfkill)

---

