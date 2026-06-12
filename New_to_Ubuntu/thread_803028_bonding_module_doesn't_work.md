---
title: "bonding module doesn't work"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by noorez on 2008-05-21
I am trying to use the bonding module for my laptop to put my wired and wireless connection together but I can't get it to work. Heres what i did:

# modprobe bonding mode=0 miimon=100
# ifconfig bond0 192.168.1.100 netmask 255.255.255.0 broadcast 192.168.1.255
# /sbin/ifenslave bond0 eth0 eth1
# route add default gw 192.168.1.1

---

### Post by noorez on 2008-05-22
bump

---

### Post by PinkFloyd102489 on 2008-05-22
This is the first thing I found in Google, albeit it's for Gentoo. Should work the same.

[http://gentoo-wiki.com/HOWTO_Setup_Bonded_ethernet_adapters](http://gentoo-wiki.com/HOWTO_Setup_Bonded_ethernet_adapters)

---

