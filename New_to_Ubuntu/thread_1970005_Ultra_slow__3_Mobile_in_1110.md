---
title: "Ultra slow  3 Mobile in 11:10"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by toft on 2012-04-30
Having done an incredibly painless install I was very impressed that my 3 mobile dongle was also  recognised and worked.

However while it is just about usable for browsing, I can't download any updates, software or drivers.

The dongle is a Huawie.  It connects instantly but never on 3G and rarely on HSDPA  (as it does in windows).  In ubuntu it usally connects on UMTS which I have never seen before.  It does occasionally manage a weak connection to HSDPA but it soon drops to UMTS and is virtually unusable.

I was hoping  something in the 300+ updates awaiting me might address the problem but the download times out.  I also need to dload Radion gfx support as its using vesa driver at the moment and the slow desktop is a nightmare.

Any suggestions on improving my connection, if possible would be appreciated.

---

### Post by toft on 2012-05-01
sudo lsusb returns:_

Bus 001 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
ubuntu@ubuntu:~$

---

### Post by toft on 2012-05-01
I think I have some minor improvement by changing APN from the default setting "3internet" to "three.co.uk".

---

### Post by toft on 2012-05-02
No consistant improvement with different APN.
 
Connects easily first time...downloads reasonably for perhaps 15mins or so.  Looses download and then is problematic to reconect.
 
Same in kubuntu, xubuntu and lubuntu!

---

