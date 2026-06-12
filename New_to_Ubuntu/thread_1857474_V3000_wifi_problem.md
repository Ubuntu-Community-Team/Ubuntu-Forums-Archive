---
title: "V3000 wifi problem"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by koolninad on 2011-10-10
Hello i am new to Ubuntu . I have installed ubuntu 11.04 version in my Compaq presario V3000 laptop before this i was using Window Xp. After installing Ubuntu I found that my Wifi card is not working i googled for this and found some post i tried all of them installed b43 drivers and firmware, removed blacklisted device, even activated my wifi card through hardware setting and download b43 5.100 something drivers. Now Its showing device is active and currently in use but i cannot fine any wireless network in range and my laptop has blue light for ON and orange light for OFF . after trying for long time it does not turned blue.... i am having b4311 wifi card and 32bit

---

### Post by bkratz on 2011-10-10
Here is the preferred method of installing software for the bcm4311 card.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by koolninad on 2011-10-12
hey thnksss thnk u very very much that process worked fine... now its only showing wireless disabled as i think i am not in my wifi range

---

### Post by bkratz on 2011-10-12
> **koolninad said:**
> hey thnksss thnk u very very much that process worked fine... now its only showing wireless disabled as i think i am not in my wifi range


Glad it helped you! Enjoy!

---

### Post by koolninad on 2011-10-14
but now m faceing another problem. Now even when my wifi switch is on the dropdown menu says wireless is disabled. now what should I do to solve this???

---

### Post by varunendra on 2011-10-17
> **koolninad said:**
> but now m faceing another problem. Now even when my wifi switch is on the dropdown menu says wireless is disabled. now what should I do to solve this???
Right-click on the Network Manager icon and make sure "Enable Networking" is ticked, and it is manually turned 'On' if there is a physical switch for it.

If these are already ok, please post outputs of:
```
lspci -nnk | grep -iA2 net
rfkill list all
```

---

