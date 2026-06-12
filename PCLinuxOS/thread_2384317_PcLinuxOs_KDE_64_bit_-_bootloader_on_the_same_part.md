---
title: "PcLinuxOs KDE 64 bit - bootloader on the same partition"
date: 2018-02-05
forum: PCLinuxOS
---

### Post by Apanta on 2018-02-05
Hello.
I downloaded and mastered PCLinuxOs 2017 - 64 bit kde.
I have this situation on my pc:
sda - data disk - ntfs
sdb - data disck - ntfs
sda  in which there are:
- sda1 - swap
- sda2 -  extended partition containing inside:
             - sda5 - Ubuntu 16.04 - ext 4
             - sda6 - Data partition in ntfs
             - sda7 - ext 4 partition where I desire install PcLinuxOs
             - sda3 - Win 10 partition - ntfs

Currently I have Ubuntu 16.04 installed in sda5 and Win 10 installed on sda3.
The boot is managed by the Ubuntu grub, installed in sda.
I launched the installation of pclos following the directions on  video, allocating it on sda7, but it does not give me the opportunity to  decide where to install the bootloader (which I want to put in sda7,  and then manage everything with the Ubuntu grub).
In fact, proceeding with the installation, a window appears where I can choose the position of the bootloader but, strangely enough, it  leaves me only three choices:
sda where Ubuntu grub2 is installed.
sdb - data disk
sdc - additional data disc.
It does not let me choose sda7 which is the partition where I installed pclos.
I do not understand why I can not install the bootloader in the same partition  (sda7) where I want to put PcLinuxOs.
I have therefore aborted the installation and here I am to ask you a little help.
Thanks in advance

ps. sorry for my poor english

---

### Post by oldfred on 2018-02-05
If it uses grub to boot, install it to the data disk. It only writes to the MBR and a few sectors after the MBR (if MBR(msdos) and not gpt).

Or you can install to drive, and then load Ubuntu and reinstall its grub to MBR. Or use Boot-Repair to reinstall grub.
       [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Apanta on 2018-02-05
Thanks for replay.
My fear is to compromise access to the data disk (eg sdb) if I install the pclos bootloader on sdb

---

### Post by Apanta on 2018-02-06
Ok thanks to all.
solved thanks to a friend (dxgiusti) as per link.
[https://www.dropbox.com/s/5y34r6pyeolcmfc/dualboot.mkv?dl=0](https://www.dropbox.com/s/5y34r6pyeolcmfc/dualboot.mkv?dl=0)

---

