---
title: "No Wireless Access"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by TheCalm101 on 2012-07-11
Hi,

I recently did a software upgrade, and once i restarted the laptop- i can no longer even scan for networks. It says that the wireless is "unplugged"? it isn't. 

This is what i get after 'iwconfig' 

lo        no wireless extensions.

eth2      no wireless extensions.

usb0      no wireless extensions.

i dont knw what to do next. I'm still a beginner

---

### Post by jemofthewest on 2012-07-11
Give us the output of:

```
lspci | grep Network
```

---

### Post by TheCalm101 on 2012-07-11
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by kurt18947 on 2012-07-11
You could start by running this in a terminal.  You can run it starting with 'sudo' in an account with 'sudo' privileges but I don't know that you have to.

```
lshw -c network
```You should get something that looks like this:

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 42
       serial: 00:00:e2:87:2c:75
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:80100000-80100fff ioport:7000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan1
       serial: 00:14:d1:e8:b6:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.28 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```This will give us an insight to your hardware.  Thanks.

---

### Post by TheCalm101 on 2012-07-11
Thank you for your continued efficient help, highly appreciated:

*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 00
       serial: 00:24:81:42:ae:f7
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:febfc000-febfffff ioport:ec00(size=256)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: ee:0f:38:eb:a3:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.9 link=yes multicast=yes

---

### Post by kurt18947 on 2012-07-11
Thanks.  There are some people well versed on Broadcom's foibles  on this site.  I am not one.  Someone should be along shortly who can get you running.  If you want, you could do a search on " BCM4312 802.11b/g LP-PHY" in the wireless and networking forum.  It would be wise to not take too seriously threads from years ago but anyone solving a problem with the same distro you're using might be worthwhile reading.

Edit:  I had one thought.  Have you checked "additional drivers"?  I believe Ubuntu offers to install some Broadcom drivers if prompted but doesn't do so by default due to licensing issues.

---

### Post by TheCalm101 on 2012-07-12
Thanx for your help. I ended up just downloading a new driver for the wireless on the "Additional drivers" sectiopn on settings. Seems to have worked perfectly. Thank you for you assistance. Much appreciated

---

