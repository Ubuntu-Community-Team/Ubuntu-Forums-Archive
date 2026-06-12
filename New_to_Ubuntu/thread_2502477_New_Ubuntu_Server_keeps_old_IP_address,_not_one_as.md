---
title: "New Ubuntu Server keeps old IP address, not one assigned by DHCP server"
date: 2024-11-16
forum: New to Ubuntu
---

### Post by NotQuiteSU on 2024-11-16
Set up a new Ubuntu Server 24 LTS device (all past ones have been upgrades for many versions). This one feels new and unfamiliar to be honest.

Initially, it took an IP address when it came online, but I want to use a different IP. My DHCP server has an assignment set, but no matter what, my Ubuntu server keeps using the old IP, even after multiple reboots.

---

### Post by outofcheese on 2024-11-17
Try
```
networkctl list
```
to identify your card, then
```
networkctl renew your-card
```
That should get you a new IP. Check in
```
/etc/netplan/<some-weird-filename>.yaml
```
if your adapter is set to use dhcp. If not you can edit that file and then
```
netplan apply
```

---

