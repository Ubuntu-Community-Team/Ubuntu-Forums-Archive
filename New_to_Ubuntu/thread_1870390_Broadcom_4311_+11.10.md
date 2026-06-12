---
title: "Broadcom 4311 +11.10"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Clinic on 2011-10-27
Hello all, I've been using ubuntu on my netbook for a while and have been loving it, so I decided to install on my main lappy. I'm now struggling with the wireless since the upgrade to 11.10. Wireless used to work fine under lucid, but not anymore. Thus, as a good little geek I googled and searched the forums, but efforts have come to naught. I stil can't get the wretched wireless going under 11.10. 

Here's my lshw -C network output:

```
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:2c:5c:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.5 latency=0 maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f2000000-f2003fff
```The hell, no driver, and i've already run

```
sudo apt-get --reinstall install bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```as well as removing any reference i can find in blacklist files to b43.

What am I doing wrong? :confused: Please help!

---

### Post by computerandu on 2011-10-27
I was having trouble with 11.04 and 4311. Then I tried some solution suggested in Ubuntu Forum which worked for me. I wrote the steps in my blog and seems it worked for many more people. Give it a try:

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by garvinrick4 on 2011-10-27
Install synaptic
```
sudo apt-get install synaptic
```open synaptic and type bcm in search:
Install the two marked and remove any that is installed other than these two in bcm. Take wired out and reboot.

---

### Post by dave0109 on 2011-10-27
On my Dell laptop with a Broadcom 4311, the BCM drivers did not work.  I had the same problem as you, both with 11.04 and 11.10.  Try removing the BCM ones, then installing the b43 drivers, as below:

```
sudo apt-get install firmware-b43-installer
```

---

### Post by Clinic on 2011-10-27
> **garvinrick4 said:**
> Install synaptic
```
sudo apt-get install synaptic
```open synaptic and type bcm in search:
Install the two marked and remove any that is installed other than these two in bcm. Take wired out and reboot.
 
Thank you so much, fixed it! :grin:
 
I would never have thought it was so simple; I think I confused myself by reading all different (and sometimes conflicting) posts, wiki entries and tips'n'tricks pages.

---

### Post by garvinrick4 on 2011-10-27
> Thank you so much, fixed it! :grin:
 
I would never have thought it was so simple; I think I confused myself  by reading all different (and sometimes conflicting) posts, wiki entries  and tips'n'tricks pages. 
Yes sometimes a nice graphic helps to understand. Welcome to the Forums hope to see you around. Enjoy your Ubuntu.

---

### Post by pauldy on 2011-11-23
Thanks this helped me too.  I have one thing to add though I had installed the STA drivers that added a file to the /etc/modprobe.d directory called broadcom-sta-common.conf.  In it were lines to ignore the b43 driver.  The file had to be deleted completely as renaming it with a different extension still loaded it.

---

### Post by hellslinger on 2012-01-03
This is probably known to people here, but I want to point out that these two drivers are different. STA is the one made by the manufacturer and the other is the open-source reverse-engineered driver. Last I knew, there were differences in how they behaved and worked. Perhaps a bug report should be filed for the STA package maintainers so that the can make the appropriate fixes.

---

### Post by itguy2012 on 2012-01-06
Hi all,
     The post from gavinrick4 worked for me as well.
     I had to remove the STA driver, reboot, and edit the blacklist.con to rem out the line blacklisting the bcm43xx.
     Finally, a post I read post to install the wicd network manager, in wicd it didnt automatically find it so I put in the preferences -- genreal tab --- wlan0. When I hit refresh it found my wireless and has been running fine ever since.
     Hope this helps.
 
C

---

### Post by MARP1961 on 2012-01-07
This also worked for me. I have never managed to get STA working on my Dell. B43 Firmware installer from Synaptic plus a reboot after a completely fresh install seems the most reliable.

Strangely, Additional Drivers seems to cause the problem in that it only offers STA and if you go ahead and install it, it causes problems with B43 (blacklisting issues). I seem to remember that in Lucid Lynx both were offered. What has changed? Why do people with these common wifi cards continue to have problems with Ubuntu? 

When I briefly tried Fedora on my son's Dell with his Broadcom card I didn't need to do any fixing. How do Fedora manage this?

---

### Post by v2kkim on 2012-05-05
> **garvinrick4 said:**
> Install synaptic
```
sudo apt-get install synaptic
```open synaptic and type bcm in search:
Install the two marked and remove any that is installed other than these two in bcm. Take wired out and reboot.
Glad I found this suggestion. I spent a while, now I am fine. Mine is ubuntu 12.  thxs.

---

### Post by Mathias25 on 2012-10-27
> **pauldy said:**
> Thanks this helped me too.  I have one thing to add though I had installed the STA drivers that added a file to the /etc/modprobe.d directory called broadcom-sta-common.conf.  In it were lines to ignore the b43 driver.  The file had to be deleted completely as renaming it with a different extension still loaded it.

Thanks for this! I have been trying forever to get this working on my HP DV6325 laptop. Followed the previous step in this thread and then deleted the file you mentioned and now it is working.

---

