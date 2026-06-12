---
title: "wireless doesn't work"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Nessta on 2008-11-07
I have a Toshiba Satellite A135-S4527

My wireless card is an Atheros 5006eg

It doesn't work natively. Can someone help me?

PS: I'm running Ubuntu Studio 8.1.0

---

### Post by bobnutfield on 2008-11-07
Wireless has been improved greatly in 8.10 with the 2.6.27 kernel.  I would have thought that that chipset would have used the ath5k module, but I could be wrong.  In  any case, you can get it working with madwifi.  Here is the tutotial:

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")

---

### Post by Nessta on 2008-11-07
That snapshots.madwifi link isn't working for me. I've come across this solution all day.

---

### Post by bobnutfield on 2008-11-07
Are there any hardware drivers listed in System>Administration>Hardware drivers?  I do not know all of the Atheros chipsets, but I have an Atheros chipset in my netboot and it works with the ath5k module in kernal 2.6.27 (which is the kernel for 8.10).  Have you tried installing the linux-backports?  Also is your wireless recognized by the system?  Type in a terminal:

> sudo lshw -C Network

or 

> lspci

---

### Post by bobnutfield on 2008-11-07
Sorry, double post

---

### Post by stainsteelcrown on 2008-11-07
I saw this thread and thought I would post.  I hope this hasn't been answered elsewhere.  I show that ubuntu is recognizing the wireless on Ibex but it says unclaimed.  I would like to change that so I can use the card.

andrew@Silas:~$ sudo lshw -C Network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:ad:0c:9f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:06:d4:92:32:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by bobosity on 2008-11-08
I'm also having this problem:

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.

Unfortunately I started following different posts to the point I don't know what I've done or what to do next.

I've got wicd going now and it reports no wireless found

I know that there many posts on this but none of them have brought me back online. It's entirely possible that I've reconfigured something and now even the correct procedure won't work.

When I did a clean install I left the cable out so that maybe it would force itself to pick up the wireless. No luck. 

I've read the post that says 8.10 will now automatically pick up the Atheros chip. Didn't work for me.

So... I'm looking for a complete checklist or tutorial. Since I've probably reconfigured something I think I need to start at the beginning.

Any pointers? ......

---

### Post by MethodOne on 2008-11-08
Try installing the package [linux-backports-modules-intrepid-generic]("apt://linux-backports-modules-intrepid-generic") and adding the following lines to the bottom of /etc/modprobe.d/blacklist:

```
blacklist ath_pci
blacklist ath_hal
```

Reboot after doing the above.

---

### Post by stainsteelcrown on 2008-11-08
[http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192)

Please use the instructions as in UserDocs/FirstTimeHowTo to compile the code, but substituting the relevant parts for acquiring the source. 

Important to remove the old modules before installing this one.

---

### Post by bobosity on 2008-11-09
Well.. that sort of worked. More was needed but mainly because I had already reconfigured everything.

Thank you

I've been running ubuntu since 5.10 and I've always had trouble with wireless. One friend would have become a convert but went back to windows for the wireless.

My machine is a mainstream laptop. When I booted the livecd it should have been on the internet immediately. If ubuntu wishes to become 'world class' this needs to be fixed. 

But anyway... I'm wireless again and I thank you all.

---

