---
title: "Mounting USB problem?"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by oibanglachele on 2013-03-24
Hi, I'm trying to mount my usb and its giving me a weird message of - **mount: /dev/sdb already mounted or /mnt/usb busy**

When I cd into /mnt/usb, I see that its empty and doesn't contain the contents of my flash drive! Its a Sandisk Cruzer U3 (if that info helps at all), and I know the machine recognizes it because when I plug it in, a bunch of text comes up that displays things like "write through" and stuff that I don't understand. Sorry for being a noob, but we all gotta start somewhere

---

### Post by westcoast01 on 2013-03-24
Had the same problem, found several posts here in the forums about this issue. For me I had to back up (copy to cd) my sandisk U3 then reformat to fat32 (I had reformatted to NTFS), remove U3 and everything worked great. Seems U3 is not compatibable with Linux. Best of luck, West.

---

