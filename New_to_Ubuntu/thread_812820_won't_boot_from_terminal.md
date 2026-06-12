---
title: "won't boot from terminal"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by xcorpbyte on 2008-05-30
Hi!

Im setting up a thin client diskless network in our school, but the thin clients won't boot.

Do I need to add the MAC address of the terminal? How about the static IP add? Im planning to use 2 servers for the 30 computers.

please help

---

### Post by quelx on 2008-05-30
Are you following this guide?

[https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto)

the mac address of a client is either printed on the physical hardware or can be found by **ifconfig** from a terminal (underlined)

```
eth0      Link encap:Ethernet  HWaddr _00:0d:43:6f:11:06_
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0

```

---

### Post by xcorpbyte on 2008-05-30
Im sorry but im new to Linux Ubuntu

i followed the guide in [http://www/edubuntu.org/GettingStarted](http://www/edubuntu.org/GettingStarted)
bur when i Turn-On the client it will display:

MAC Add
DHCP......

then 

Insert boot disk

---

### Post by quelx on 2008-05-30
Each thin client needs a line in **/opt/ltsp/(ARCH)/etc/lts.conf/lts.conf** (where **(ARCH)** is **i386** or **amd64** depending on which version you installed.  You can get the MAC address, [00:11:25:84:CE:BA], information from each of the client machines.  I'll be you see it when the terminal is trying to boot, if not boot a live CD and get it from **ifconfig** as above.

---

### Post by xcorpbyte on 2008-05-30
Thank you so much for your help quelx, its now working

---

