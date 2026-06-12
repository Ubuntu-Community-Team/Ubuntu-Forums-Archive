---
title: "Windows 7 is not showing up in GRUB"
date: 2015-10-03
forum: New to Ubuntu
---

### Post by faraz_k86 on 2015-10-03
Ive recently got this new system and have installed Windows and Kubuntu on it. It has an SSD and a normal HDD. I'm using the SSD for booting and HDD for file storage etc.

I installed Windows 7 first and once it installed I installed Kubuntu (as I always do) It usually detects the other OS and I rarely have any problems. But this time after I installed Kubuntu Windows could not be loaded or found. After a restart GRUB shows up but the Windows option is not present there, only Ubuntu is selectable.

I used Boot Repair but it did not solve my problem, here is the output of the boot-repair process: [http://paste.ubuntu.com/12648497/](http://paste.ubuntu.com/12648497/)

---

### Post by faraz_k86 on 2015-10-03
A simple sudo update-grub fixed it. I did not need any extra tools after all

---

