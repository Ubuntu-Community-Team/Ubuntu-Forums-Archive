---
title: "wireless drivers for linus system"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Leroy317 on 2008-07-17
I have just installed linux system on my HP Pavillion dv6000. and found out that HP does not have wireless drivers for linus system.  can someone help me get wireless drivers that would run on the linus system. Thanks. Leroy317

---

### Post by hyper_ch on 2008-07-17
wel, first you'd need to tell what chip you have on your card and then you can search for it.

---

### Post by Otto-C on 2008-07-17
provide the output of the following from your linux system:

sudo lspci -nn
sudo iwconfig
sudo ifconfig
sudo lshw -C network

---

