---
title: "Setting up a wireless network in Ubuntu."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by rdg11 on 2008-08-05
I have a Broadcom 802.11b/g WLAN card and a Netgear 108 mbps wireless router. I am very very new to Ubuntu, and I cannot figure out how to get Ubuntu to recognize my wireless network. I really need to know how to set this up from step 1, because from browsing it seems like there may be a lot that goes into it (some even finding a list of network based off of Windows networks?). I'm just confused on it, and any help would be immensely appreciated, I know barely anything about computer networking.

---

### Post by Ryadt on 2008-08-05
Try to see if your card is in System > Administration > Hardware Drivers. If it is, then enable it. Else post the output of ```
lshw -C network
```

---

### Post by superprash2003 on 2008-08-05
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

