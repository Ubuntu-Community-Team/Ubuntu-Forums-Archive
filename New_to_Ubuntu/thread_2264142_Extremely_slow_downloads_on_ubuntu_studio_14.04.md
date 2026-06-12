---
title: "Extremely slow downloads on ubuntu studio 14.04"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by conor6 on 2015-02-05
Hi, I recently installed ubuntu studio 14.04, getting rid of windows due to my disliking of windows. Although I have noticed that while my internet speed is OK (although can slow down at times, nothing too major) my download speed is really slow, going as low 50kbs. Also this is only on the wifi, when I use the ethernet it's fine.

 I'm new to linux, with my only experience being playing around with main ubuntu a bit.
I'm using a Lenovo z575 which has a ralink rt3090 wireless card.

I really hope I can get some help with this as the laptop is my only computer, I use it in class and use cloud storage for a lot of files so its a lot of downloading and uploading.

here are the results of lshw -C network if its any help:
```

mochaci@mochaci-Ideapad-Z575:~$ sudo lshw -C network
[sudo] password for mochaci: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:c3:a3:28
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 64:27:37:54:cd:d7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-45-lowlatency firmware=0.34 ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff
```

Many thanks again.

---

### Post by verymadpip on 2015-02-06
Hi there.
I'm hopeless with networking, but a quick search on that there interwebs suggests the RT3090 can be a bit of a funky piece of kit.

This thread is pretty ancient so I don't know how much help it'll be:
[http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498)  (Post #3 looks like a good place to start).

Good luck & hopefully someone more knowledgeable than me will turn up to help soon.

---

### Post by cuteboi on 2015-04-20
I'm in the same boat, so I updated everything and even did a dist-upgrade, and that destroyed everything else.

I'm in the progress of looking for help, but this wlan issue is one of those issues, so adding this reply to let others know that it's a problem that is also experienced when upgrading.

I lost Video/Graphics in the process, but I can hear the sounds playing in the background.

---

### Post by nathanservicesinc2 on 2015-04-20
Two things come to mind; (1) you might try LUBUNTU on that system rather than UNBUNTU;;  LUBUNTU is the Lightweight version UBUNTU (2) I use an Airlink 300 m/b/s network adapter to help speed things up.  on a third note you may need to go in and reconfigure your kernels cpuinfo files to reconfigure settings that will allow larger files to download.

---

