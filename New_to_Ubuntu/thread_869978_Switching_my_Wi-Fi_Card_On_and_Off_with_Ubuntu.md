---
title: "Switching my Wi-Fi Card On and Off with Ubuntu"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by The Browncoat Cat on 2008-07-25
Under Windows, switching the built in RealTek 8187b WI-FI card is achieved by holding down the "FN" key and pressing "F10".  This does not work under Ubuntu.  Could somebody please tell me the command I needed to type into a terminal window to toggle my Wi-Fi on and off.  Also is it possible to map this command to the same keyboard shortcut as Windows.

Thanks in advance.

---

### Post by gimlithedwarf on 2008-07-25
open a terminal and:
first type ```
ifconfig
``` to find out the name of your wifi card it will be something like wifi0 or ath0 then to turn it off type ```
sudo ifconfig *interfacename* down
``` and to turn it on type ```
sudo ifconfig *interfacename* up
```

---

### Post by gimlithedwarf on 2008-07-25
oops for repost

---

### Post by The Browncoat Cat on 2008-07-25
> **gimlithedwarf said:**
> open a terminal and:
first type ```
ifconfig
``` to find out the name of your wifi card it will be something like wifi0 or ath0
This produces results for "eth1" and "lo".  As I understand it, and I might be wrong (I probably am) because the card is switched of it will not give its name with the command "ifconfig"

---

