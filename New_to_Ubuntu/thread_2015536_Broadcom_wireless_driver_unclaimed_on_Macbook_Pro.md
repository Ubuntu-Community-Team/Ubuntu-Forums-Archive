---
title: "Broadcom wireless driver unclaimed on Macbook Pro"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by porterrakter on 2012-07-03
I'm new to Ubuntu and I'm running 12.04 LTS 64 bit which I downloaded recently to dual-boot with OS X Lion on my Macbook Pro (bought new in fall 2011).  I'm having problems making the wireless work, even after downloading and installing drivers I've found on other forums/the general internets.  My controller as identified in Terminal with "lspci" is as follows:

```
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
```And the results of "sudo lshw -C network"
```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: c8:2a:14:4a:2b:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=57765-v1.37 ip=10.4.112.20 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:b0400000-b040ffff memory:b0410000-b041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:b0600000-b0603fff
```If I reboot my computer the second "*-network" has an "UNCLAIMED" after it, but after I type in "sudo modprobe b43" it goes away until I reboot the computer again.  However, even after loading the b43 module I still get this output to "sudo iwconfig"

```
lo        no wireless extensions.

eth0      no wireless extensions.


```If there's any more info you need to help figure this out, let me know.  Thanks!

EDIT: I just realized that this should probably go in the networking and wireless forum...I didn't see it before I posted and I don't think I can move this thread...sorry about that.

---

### Post by Bucky Ball on 2012-07-03
Welcome.

Try installing firmware-b43-installer also (I think that's it).

If you get online and do update, what do you have in 'Additional Drivers'? Try that first.

PS: Just looked here:

[http://au.altavista.com/search;_ylt=A7exU8EwLvNPdW0A6DlaC1B.?p=BCM4331%20ubuntu&fr=altavista&fr2=sfp](http://au.altavista.com/search;_ylt=A7exU8EwLvNPdW0A6DlaC1B.?p=BCM4331%20ubuntu&fr=altavista&fr2=sfp)

... and there's tons of info. Sift away.

---

### Post by porterrakter on 2012-07-03
I think I already installed that, but just in case I tried it again with "sudo apt-get install firmware-b43-installer" and I got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

If there's a way to search for and install drivers without using terminal, I have yet to find it.  If I use "Additional Drivers" under System Settings, it does an automatic search for me without coming up with anything.

I'll take a look at those search results, but I think at this point it might be best if I get the help of someone more experienced than I.  I've already spent several hours trying to get a fix for this without posting.  Thanks for the reply though.

---

### Post by porterrakter on 2012-07-03
Solved!  Thanks for your help, but this post solved my problem:

[http://ubuntuforums.org/showthread.php?p=12058947#post12058947](http://ubuntuforums.org/showthread.php?p=12058947#post12058947)

Now...off to figuring out the rest of Ubuntu.

---

