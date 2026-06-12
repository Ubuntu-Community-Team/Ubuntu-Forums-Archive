---
title: "HowTo: fix Hal.dll error after ubuntu installation"
date: 2007-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ukripper on 2007-06-06
I had the same problem. Error message you get is very misleading it should be boot.ini not hal.dll but anyhow, I have resolved it by following steps:

**Please Note : This HowTo is not for every case but for corrupt hal.dll error message only**

1. Boot into XP Cd.
2. Go to recovery
3. Recovery console type: **bootcfg /rebuild**  and then press enter
4. The first prompt asks Add installation to boot list? (Yes/No/All )  Type **Y** press enter
5. Enter Load Identifier:: Windows XP press enter
6. Enter OS Load options:.
Type** /Fastdetect**  and press Enter. 
7. Exit and reboot.

Goodluck.

---

### Post by doppis on 2007-12-26
I am having the same problem but I am installing xp on a external harddrive not a partition from my internal hd in my laptop.  I have tried your solution but it still doesn't work, hal.dll is still missing/corrupted.

---

