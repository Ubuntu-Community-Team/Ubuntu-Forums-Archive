---
title: "installing ubuntu 14.04.2 LTS alongside win 8"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by m0nk3n on 2015-03-24
hello :) i have windows 8.1 pro on a hdd. while i got win7 ultimate on a ssd.

i know how to install ubuntu since i had a dual boot of win 8 and ubuntu before. using the something else option. but then accident struck and i had 3 windows boot loaders and a grub loader :P

if i choose the option "install alongside win 8" will it automatically choose the partition i set aside for it to be installed on? or do i have to go into "something else"? if i have to, what would be my choices in there? and how much space should i set aside for it and the files ?

---

### Post by oldfred on 2015-03-24
Only use Something Else. See link in my signature for a Caution on any other install option.

And if you have two drives, you need to specify which drive for install and which for boot loader. Generally you want Ubuntu boot loader on same drive as Ubuntu install, but all auto install options just put boot loader on drive seen by UEFI/BIOS as sda.

Are your current installs UEFI or BIOS?
Windows only boots with UEFI from gpt partitioned drives, and only from BIOS(CSM) with MBR(msdos).

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by m0nk3n on 2015-03-25
i think its uefi. i have a rampage IV extreme motherboard. popped the dvd in and installed win 8. burned 14.04.2 LTS on a dvd ready to install.

how big should the space be? i have alot of games on steam, origin, battlenet etc, i would like to install eventually.

btw. 24 gig of mem.

last time i installed ubuntu after i installed win 8 i used the something else option, then i fiddled with that for about 6 hours and said myself finished with it cause i just couldnt find the option to install ubuntu by choosing that partition and ok on it.

edit: reading install procedure :)

---

### Post by oldfred on 2015-03-25
Do not know about games and how much space they may need.

My / (root) system uses about 11GB including 2GB for /home with Picassa in .wine. But all data is in /mnt/data partition on another drive. My boot drive is a SSD and my data drive is a HDD.
Many install with a separate /home partition on the HDD and I believe you can install games in /home not directly in / partition if /home not in /.

It is my understanding that games can be installed in /home but if in .wine that just about has to be in / (root) as that is difficult to relocate. So you may want a large / partition.

With 24GB of RAM, you may never use swap, but I like to configure with 2 or 3GB just to have some.

 ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

I just built new system with Asus AR and had lots of issues getting all the UEFI settings correct so it would boot installer in UEFI mode. I also made sure to turn off UEFI fast boot on reboot until all configuration was done and changed cold boot to normal not fast boot. I change fast boot to 3 sec delay so I could get into UEFI if needed. I had to change from Windows to Other, which I think turned off secure boot. And then under CSM was the rest of the UEFI settings.
       
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by m0nk3n on 2015-03-25
sound blaster z not supported... found some sound fixing commands which purged my whole settings section of the ubuntu so that i could think that i fixed the sound but it wasnt broken.

no matter though, after your explanation and some thinking i know how to next time.

but now i'm stuck with the grub which i must remove first which i know how. dvd of win 8 and all that...

---

### Post by oldfred on 2015-03-25
If it is UEFI, you should just be able to go into UEFI and select Windows as new default.

And if UEFI and you want to totally remove grub/ubuntu UEFI entries, you have to delete folder in efi partition first or it will get added back to UEFI menu and then delete UEFI menu entries with efibootmgr. Details on procedures in link in my signature below.

But if you reinstall in UEFI mode, then that install will overwrite the current grub folder in the efi partition. You may get another entry in UEFI menu, and want to houseclean that.

---

### Post by m0nk3n on 2015-03-26
oh.. i looked at a uefi installation of windows 7 on youtube. i guess its not uefi. its just normal installation.

did bootrec in "repair windows", i'll install ubuntu at a later time.

you answered my question in full by your first post so i guess its complete. thanks. :)

---

