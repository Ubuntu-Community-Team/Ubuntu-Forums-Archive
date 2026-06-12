---
title: "Proprietary Broadcom 802.1.1 Linux STA wireless driver problem"
date: 2016-02-27
forum: New to Ubuntu
---

### Post by rob162 on 2016-02-27
Lubuntu 15.10 just installed Only OS on Dell Mini 1010 Ethernet has connection Software and updates
When applying changes for use of Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)  The change status bar starts out at about 1/4", does not move, and Do not use the devise is automatically chosen.
Device that is not working is
Broadcom Corp BCM4312 802.11b/g LP-PHY (wireless 1397 WLAN Mini-Card)

---

### Post by sandyd on 2016-02-27
Make sure you are connected to the internet and open a terminal, and run
```

sudo apt-get install --reinstall bcmwl-kernel-source

```

Are there any error messages, and does it stall when installing it in this method?

---

### Post by rob162 on 2016-02-27
worked ok. Trying to find list of SSID. Will update on WiFI connection  progress

---

### Post by sandyd on 2016-02-27
Fixed typing error.

---

### Post by rob162 on 2016-02-28
I am finally on the WiFi internet. Thanks.  I spoke too early see next message

---

### Post by rob162 on 2016-02-28
lubuntu was too lite, I erased disc, installed xubuntu 15.10. Installation went ok. Same Broadcom proprietary driver problem. **WiFi connection worked on trial version**, but not on installed version. Tried the code you mentioned that worked with lunbuntu. 3 times came up "bcmwl cannot be authenticated", when I continued  "unable to fetch some archives"  4th try, erased and reinstalled Xbuntu 15.10, had **WiFi connection during install**. Now, no connection, same proprietary driver problem, and bcmwl package still can not be authenticated

---

### Post by jim_deadlock on 2016-02-29
During Ubuntu installation it's highly recommended to use a wired connection if at all possible. Running updates often resolves wifi driver issues so you can then unplug and use the wifi.

---

### Post by rob162 on 2016-02-29
It worked. I reinstalled Xbuntu 15.10, checking to check for updates, with an Ethernet connection. Thank you from a frustrated Linux novice ready to go back to that dreaded Microsoft.

---

