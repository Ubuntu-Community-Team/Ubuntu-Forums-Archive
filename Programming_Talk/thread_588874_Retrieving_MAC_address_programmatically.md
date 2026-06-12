---
title: "Retrieving MAC address programmatically"
date: 2007-10-23
forum: Programming Talk
---

### Post by HunterSBuntu on 2007-10-23
Does anyone have any recommendations on how to retrieve a MAC address programmatically?

So far I'm looking at doing a system call to **ifconfig**, piping that and parsing the output to get the MAC address. I can't help but feel that there should be a more elegant way of getting this info that I may have overlooked.

Are there any other methods that I can use to query network hardware for this sort of information?

---

### Post by FXEF on 2007-10-23
> **HunterSBuntu said:**
> Does anyone have any recommendations on how to retrieve a MAC address programmatically?

So far I'm looking at doing a system call to **ifconfig**, piping that and parsing the output to get the MAC address. I can't help but feel that there should be a more elegant way of getting this info that I may have overlooked.

Are there any other methods that I can use to query network hardware for this sort of information?

This will list your MAC.

/sbin/ifconfig | grep HWaddr

here's another way

lshw | grep serial

FXEF

---

### Post by angustia on 2007-10-23
cat /sys/class/net/ath0/address

---

### Post by stair314 on 2009-05-10
You could install libnet and use libnet_get_hwaddr().

---

