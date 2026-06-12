---
title: "Functional BCM4306 on AMD64"
date: 2005-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by eggshape on 2005-09-11
hi, hope this helps someone:

i got my internal wireless card (BCM4306 802.11b/g) working on an ASUS Z80K(AMD64):

1. download the latest ndiswrapper source tarball from sourceforge (1.3rc1)
2. get the 64-bit windows drivers from Linuxant (released from Broadcom, BCMWL564 NDIS driver)
3. follow the directions in the Wiki for ndiswrapper installation
4. i configured my card by editing /etc/network/interfaces with 

iface wlan0 inet dhcp
wireless-essid your_net
wireless-key your_key

you can ifup your card or add "auto wlan0" as the 1st line.

PS: the ndiswrapper module compiled from the kernel-2.6.11 source does not work; just replace it with the one that you compiled from sourceforge;  i tried this before without success - i think it's a combination of the new ndiswrapper version and the drivers from Broadcom.

good luck,
alex

---

