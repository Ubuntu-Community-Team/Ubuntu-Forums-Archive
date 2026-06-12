---
title: "RTL8 Wireless USB SOLUTION!"
date: 2011-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Spyderkid on 2011-01-20
[SIZE=3][COLOR=SeaGreen]
[COLOR=Red]UBUNTU 10.04 & 10.10 (you won't have this problem in 11.04)[/COLOR]

How to fix your currently not working RTL8192SU chipset Wireless Adapter...
It's very simple...

just enter these in a terminal...
```

sudo cp -R /lib/firmware/RTL8192SE /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```[COLOR=Blue]and restart the computer!

DONE![/COLOR][/COLOR][/SIZE]

---

### Post by Spyderkid on 2011-01-29
if you read this post before when this comment was posted you may want to look at it again, i've changed alot of things

---

### Post by TheHackOps on 2011-01-29
Not tested since i don't have said hardware but thanks for your effort im sure people will appreciate it

---

### Post by Spyderkid on 2011-01-29
ok ill try to continue to update it :)

---

### Post by Spyderkid on 2011-01-29
This does work for the RTL8192SU chipset but should work for most other rtl8 chipsets as well.

---

### Post by Spyderkid on 2011-03-07
[EDIT]
Comment...

Changed the whole way to make driver to a much simpler solution!

---

