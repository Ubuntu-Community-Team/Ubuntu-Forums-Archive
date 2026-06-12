---
title: "Can't see my Harddrives"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by cyrus6789 on 2008-06-10
Hello I'm almost completely new to linux and am trying to install Ubuntu 8.04 64 bit on my desktop. It runs the live CD fine with a few of those I/O errors but those are due to my floppy. My real problem is when I try to install it gets to the partition screen and I cannot see anything. Nothing shows up on the list. My harddrives are SATA and plugged into the motherboard. They can be seen from the BIOs. I have even tried switching them around to different ports but still nothing. Help please.

---

### Post by gr4nf on 2008-06-10
try:
```

sudo mount /dev/sda /mnt

```
while booted into a live cd.

---

### Post by cyrus6789 on 2008-06-10
i tried that and it simply says special device does not exist

---

### Post by nhasian on 2008-06-10
Hello Cyrus6789,

I'm not sure what your problem is, but i have two things you can do to troubleshoot:

1) try setting your hard disks to SATA 1.5G instead of the 3.0G.  depending on the manufacturer, it may just be a physical jumper on the drive you have to add or remove, or you may need to download a tool from the manufacturer to change the setting in the drive's firmware.

2) Just out of curiosity, have you tried installing the Ubuntu 8.04 32-bit version?

> **cyrus6789 said:**
> trying to install Ubuntu 8.04 64 bit on my desktop. ...My real problem is when I try to install it gets to the partition screen and I cannot see anything. Nothing shows up on the list. My harddrives are SATA and plugged into the motherboard.

---

