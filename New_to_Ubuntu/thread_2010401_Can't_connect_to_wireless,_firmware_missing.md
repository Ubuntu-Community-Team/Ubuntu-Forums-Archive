---
title: "Can't connect to wireless, firmware missing"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by NumberNine on 2012-06-25
Hi, I'm new to Ubuntu and I need some help. I'm getting the missing firmware for wireless Internet. I'm on a Dell laptop by the way. After reading a lot of this thread, I did:

lucas@ubuntu:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Hopefully that gives you the information needed to fix the problem. Thanks!

---

### Post by oldos2er on 2012-06-25
Post moved to its own thread.

---

### Post by NumberNine on 2012-06-25
OK, and thanks.

---

### Post by NikTh on 2012-06-25
From terminal 
```
jockey-gtk
``` and install STA driver.. if its there.
Reboot.

---

### Post by NumberNine on 2012-06-25
Thank you so much, that fixed the problem!

---

