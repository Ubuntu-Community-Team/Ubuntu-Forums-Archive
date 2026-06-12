---
title: "Internet does not work"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ZomGie75 on 2008-04-25
This is my first time using Ubuntu.  I just partitioned my iBook to boot Mac OS X and Ubuntu 8.04.  The internet doesn't work when I'm in the Ubuntu partition.  I looked around as much as I could, but couldn't find anything that helped.  It says there is a 0% connection to my wi-fi.  I tried a wired connection, and that didn't work either.  Is there a specific way to connect to the internet using Ubuntu?

If you need more info, please ask.

-----------
- G4 iBook
- Apple Airport
-----------

---

### Post by Mazza558 on 2008-04-25
> **ZomGie75 said:**
> This is my first time using Ubuntu.  I just partitioned my iBook to boot Mac OS X and Ubuntu 8.04.  The internet doesn't work when I'm in the Ubuntu partition.  I looked around as much as I could, but couldn't find anything that helped.  It says there is a 0% connection to my wi-fi.  I tried a wired connection, and that didn't work either.  Is there a specific way to connect to the internet using Ubuntu?

If you need more info, please ask.

-----------
- G4 iBook
- Apple Airport
-----------

In the Ubuntu terminal, type in 

```
lspci
```

and tell us the model of wireless card.

---

### Post by ZomGie75 on 2008-04-25
Should be the same as the one that the mac uses, so i just grabbed the info from the mac info:

```
AirPort Card Information:
  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	405.1 (3.90.34.0.p18)
  Current Wireless Network:	____________
  Wireless Channel:	1
```

---

### Post by cubeist on 2008-04-25
> **ZomGie75 said:**
> Should be the same as the one that the mac uses, so i just grabbed the info from the mac info:

```
AirPort Card Information:
  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	405.1 (3.90.34.0.p18)
  Current Wireless Network:	____________
  Wireless Channel:	1
```

yes, but, the point of running lspci is to show whether your computer recognizes the airport card in linux...

---

### Post by ZomGie75 on 2008-04-27
```
0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN controller (rev 02)
```

I found some other help file stuff that said to go to drivers, and enable it.  I tried to do that but it said I needed software that i needed to download or something.  I haven't tried to do a direct connection yet, i'll try that now.

**Edit:** 
Direct wired connection works on DHCP.

---

