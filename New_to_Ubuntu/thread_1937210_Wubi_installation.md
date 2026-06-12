---
title: "Wubi installation"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by TimCor on 2012-03-07
Hi All
Previously I successfully ran WUBI on an XP machine. Now I have WIN7 running on an SSD (120GB) as the C drive (68gb free). With a 1TB hard disk drive D (679GB free). i7 2700k processor.

I have tried to install Ubuntu using WUBI on both disks (separately) but get the same error message near the end of installation saying look at log wubi 11.10 rev245 - which does not give a beginner like me a simple reason for failure. I can add this log to any reply.

Hoping that you can help

Tim

---

### Post by NikTh on 2012-03-07
Wubi its a virtual installation .Personaly i don't trust it. Creates lot of problems. I suggest to do a dual boot of ubuntu and xp. By the way to install from wubi you must do it ( i m not sure , but i think) to the drive that you have xp. Example : if your xp are in ssd you must install wubi there. not to 1Tb hdd. (i repeat i am not sure about that). And i don't know if wubi can handle ssd. Maybe cannot. 
But i am sure for my suggestion. Dual boot is much much better and reliable.

---

### Post by TimCor on 2012-03-07
Many thanks for the very quick reply. I am running Win 7 professional on the SSD. I have tried installing on both the SSD card (same as Windows) and on the Drive D option in the initial start window, both caused the same error. I appreciate WUBI is likely to be more unstable, but had great success with it in XP in the past. If all else fails can I partition the D drive and install a version of UBUNTU there (away from Windows on the SSD card)??

All the best

Tim

---

### Post by NikTh on 2012-03-07
> **TimCor said:**
> If all else fails can I partition the D drive and install a version of UBUNTU there (away from Windows on the SSD card)??

All the best

Tim

of course you can install ubuntu anywhere you want. Alongside windows or  not . I would installed  ubuntu in D drive . But you must have the  option to boot from that drive (D). I think you have it. Windows are incapable to recognize  ubuntu as operating system . But if you boot from D drive you will see that grub(Gnu/Grub bootloader) has this option(to boot to windows and ubuntu)

Install ubuntu properly (not wubi) and you will see . Another experience > Faster , more stable... !!

---

### Post by Mark Phelps on 2012-03-07
I would recommend the following approach:
1) You need some unallocated space on the hard drive containing the "D" partition (MS still insists on calling Partitions "drives")
2) Burn a CD or create a USB stick with an installable version of Ubuntu.
3) Disconnect the SSD
4) Boot from the Ubuntu CD/USB stick and install to the hard disk.  Also let it install GRUB by default there.
5) Reboot your PC and confirm that you can get into Ubuntu OK
6) Shutdown the PC, reconnect the SSD -- but continue to boot from the hard drive.
7) When Ubuntu comes up, open a terminal and enter "sudo update-grub"  This will regenerate the GRUB menu and add an entry for Windows.
8) Reboot the PC.

You should now get a GRUB menu and be able to choose between Ubuntu and Windows.

---

### Post by bcbc on 2012-03-07
> **TimCor said:**
> Hi All
Previously I successfully ran WUBI on an XP machine. Now I have WIN7 running on an SSD (120GB) as the C drive (68gb free). With a 1TB hard disk drive D (679GB free). i7 2700k processor.

I have tried to install Ubuntu using WUBI on both disks (separately) but get the same error message near the end of installation saying look at log wubi 11.10 rev245 - which does not give a beginner like me a simple reason for failure. I can add this log to any reply.

Hoping that you can help

Tim

It's probably bug [lpbug]862003[/lpbug]. You can check the log file to confirm this. (If it is then the install was successful).

---

### Post by TimCor on 2012-03-09
I would like to thank everyone for their help over this question, but at the moment the solutions do not seem practical. I will try using a bootable USB stick

Again many thanks

TimCor

---

