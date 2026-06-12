---
title: "No network on esxi 4.1 &amp; ubuntu 12.04 VM"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by jat421 on 2012-04-30
Hi, I am new to linux and installed the 12.04 on a new VM running esxi4.1. It doesn't seem to be picking up the ip address. Here are the few things checked.

ifconfig gives a eht0 and lo interfaces and the eth0 has no IP address.

If I add 
```

auto eth0
iface eth0 inet dhcp

```and restart the networking it says ignoring unknown interface eth0=eth0

The dmesg command gives eth0: no IPv6 routers present. Could that be the issue?

---

### Post by jat421 on 2012-04-30
I think it's working now. Had to set the IP to manual. Thanks

---

