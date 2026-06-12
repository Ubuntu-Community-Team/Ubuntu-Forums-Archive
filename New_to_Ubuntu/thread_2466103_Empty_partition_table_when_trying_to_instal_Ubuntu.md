---
title: "Empty partition table when trying to instal Ubuntu 18.04"
date: 2021-08-19
forum: New to Ubuntu
---

### Post by c145dee on 2021-08-19
I have created Ubuntu bootable media and chosen the Try Ubuntu option, then clicked on the Install Ubuntu icon but I have a problem at the partitioning menu.  There is no partition to instal to. If I click on + to add to the partition table then instal crashes out with the following error:
ubiquity crashed with TypeError in partman_dialog()
My laptop is a Dell XPS 13 which was purchased with Ubuntu pre-installed.
Dell Support have asked me to re-instal Ubuntu after I had an issue one day when, on startup, it came up with ".... please run SETUP program, Time-of-day not set"  I entered setup and set the date, but then it would only boot to initramfs shell.  
Is the problem with the empty partition table on the instal anything to do with the RAID setup?

---

### Post by ajgreeny on 2021-08-19
It sounds as if the easiest way for you to overcome this would be to use gparted in the live system, the Try Ubuntu that you mentioned, go to Device in the menus and choose to create a new partition table, then you should be able to use the + and create whatever partitions that you want.

---

### Post by tea for one on 2021-08-19
> **c145dee said:**
> Is the problem with the empty partition table on the instal anything to do with the RAID setup?

Do you have two disks in your PC?

If there is only one then, the Sata mode should be AHCI (in UEFI set-up).

---

### Post by c145dee on 2021-08-20
I have only one drive  - 1TB M.2 PCIe NVMe Solid State Drive

---

### Post by tea for one on 2021-08-20
Have you followed the advice suggested by [COLOR="#0000FF"]ajgreeny[/COLOR] in post 2?

While you are in a live session, please check that you have booted in UEFI mode?
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Also, when preparing a partition table, GPT (rather than msdos) is the modern choice.

---

### Post by c145dee on 2021-08-20
Thank you very much for your help.  In the setup, I chose System Configuration -> Sata Operations -> SELECT AHCI.  I was then able to complete the installation.

---

### Post by c145dee on 2021-08-20
Thanks you for your advice.  Before I tried your suggestion, in the System Configuration  I changed SATA mode from RAID ON to AHCI.   I was then able to complete the installation successfully.

---

### Post by tea for one on 2021-08-20
Excellent - We all like a successful outcome.
Thank you for marking the thread as solved, it helps other forum searchers.

---

