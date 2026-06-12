---
title: "Detecting IP address from Mac Address - Linux"
date: 2010-06-10
forum: Programming Talk
---

### Post by COKEDUDE on 2010-06-10
Can anyone get this to work? 
```
ip neigh flush all > /dev/null; # Clears out your arp cache
fping -c 1 -g -q 192.168.1.0/24 2> /dev/null;  # pings all of subnet
arp -n | grep "00:1B:4C:22:28:B1"   # Search cache for MAC address
```
[http://programminglinuxblog.blogspot.com/2007/11/detecting-ip-address-from-mac-address.html](http://programminglinuxblog.blogspot.com/2007/11/detecting-ip-address-from-mac-address.html)

---

### Post by Milliways on 2010-06-10
> **COKEDUDE said:**
> Can anyone get this to work? 
```
ip neigh flush all > /dev/null; # Clears out your arp cache
fping -c 1 -g -q 192.168.1.0/24 2> /dev/null;  # pings all of subnet
arp -n | grep "00:1B:4C:22:28:B1"   # Search cache for MAC address
```
[http://programminglinuxblog.blogspot.com/2007/11/detecting-ip-address-from-mac-address.html](http://programminglinuxblog.blogspot.com/2007/11/detecting-ip-address-from-mac-address.html)

This is unlikely to work unless you have a NIC with MAC "00:1B:4C:22:28:B1"

Just try "arp -n"

---

### Post by rnerwein on 2010-06-10
hi
i guess you have to use: 
arp -n | grep "00:1[COLOR=Red]b[/COLOR]:4C:22:28:[COLOR=Red]b[/COLOR]1"    # lower b not capital or
arp -n | grep [COLOR=Red]-i [/COLOR]"00:1B:4C:22:28:B1"

ciao

---

