---
title: "ethernet port stopped working after installing wifi drivers"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by kalimojo on 2011-12-22
my ethernet port stopped working after installing wifi drivers for the ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe

wifi is working but ethernet is dead.

any ideas ?

[FONT=Bitstream Vera Sans Mono]Ignoring unknown interface eth0=eth0.

[/FONT]
 Note that I do have eth0, and "ifconfig" shows that it is up and has been assigned an IP.
 To fix the error, check the file /etc/network/interfaces, comment out the unwanted interfaces, and keep at least the following:
 [FONT=Bitstream Vera Sans Mono]auto lo
iface lo inet loopback[/FONT]
 auto eth0
iface eth0 inet dhcp

---

