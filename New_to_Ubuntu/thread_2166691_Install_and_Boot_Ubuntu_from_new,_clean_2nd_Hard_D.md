---
title: "Install and Boot Ubuntu from new, clean 2nd Hard Drive? (Master Drive Windows)"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by redrider5050 on 2013-08-10
Hi Everyone, this is my first attempt at using Ubuntu in lieu of Windows. 
Am in process of installing 2nd hard drive in desktop. Was hoping to boot Ubuntu off new drive as to ensure no fallout with the Windows currently running my programs and apps.

Good idea? My only experience with ubuntu/ linux was to restore my windows when all other hope was lost! 

Thanks.

---

### Post by ant2 on 2013-08-10
Yes good idea. I used to have windows and linux on separate drives. You can remove your windows drive whilst you install Ubuntu on your new drive then pop your windows drive back in set the Ubuntu drive as primary boot in bios then update grub in Ubuntu and then you get a dual boot system.

---

### Post by Linux90s on 2013-08-10
Just be aware that newer systems support UEFI and if your new system supports it, that you must select Legacy or UEFI as your preferred booting method. 
UEFI and GPT are needed for the larger hard drives (3TB+) to be able to boot an o.s.

---

### Post by redrider5050 on 2013-08-10
Sounds good, and safe. Thanks.

---

### Post by redrider5050 on 2013-08-10
I assume the settings for UEFI are in the system bios settings? Not sure if newer means this year or past 5 years.... the machine is about 5 yrs old;Gateway GM5446e stuck with the non-supported Win Vista. ( Cant even get service pack 1 back after replacing last hdd.)

---

### Post by ant2 on 2013-08-10
I'm fairly sure your machine is not UEFI.

---

### Post by redrider5050 on 2013-08-10
Guess I deserved that one. A little research goes a long way...if I have BIOS, I definitely do not have UEFI as the latter takes the place of a BIOS type system in some of the newer hardware configurations.
Any benefit from trying out the os prior to hard install on 2nd drive as described above?

---

### Post by ant2 on 2013-08-10
I would certainly take advantage of the live session offered on a Ubuntu CD/USB to check your hardware such as graphics and Wifi are playing ball before you install.

---

