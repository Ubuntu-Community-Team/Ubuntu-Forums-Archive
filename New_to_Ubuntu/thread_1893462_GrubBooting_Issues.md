---
title: "Grub/Booting Issues"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by djevans3 on 2011-12-10
Hi, I'm having some boot problems and hoping someone can help me.  My drive config is:

sda1 - 11.10 Ubuntu
sda2 - ext4 blank
sda3- NTFS file storage
sdb1 - NTFS XP Home

I had this configuration up and running, then decided to wipe sdb1 and do a fresh install of windows xp. Of course it wiped grub.  I tried using Boot Repair by booting to ubuntu on a thumbdrive and letting it automatically repair my booting records.  It successfully loaded grub because the boot menu comes up, however, when I select to run Ubuntu, it won't load.   My concern is it may be pointing to the Ubuntu on the thumbdrive (sdc1) instead of the install on sda1.  Below is a link to the log.  Any help is appreciated!!!

[http://paste.ubuntu.com/765873/](http://paste.ubuntu.com/765873/)

---

### Post by fantab on 2011-12-10
> **djevans3 said:**
> Hi, I'm having some boot problems and hoping someone can help me.  My drive config is:

sda1 - 11.10 Ubuntu
sda2 - ext4 blank
sda3- NTFS file storage
sdb1 - NTFS XP Home

I had this configuration up and running, then decided to wipe sdb1 and do a fresh install of windows xp. Of course it wiped grub.  I tried using Boot Repair by booting to ubuntu on a thumbdrive and letting it automatically repair my booting records.  It successfully loaded grub because the boot menu comes up, however, when I select to run Ubuntu, it won't load.   My concern is it may be pointing to the Ubuntu on the thumbdrive (sdc1) instead of the install on sda1.  Below is a link to the log.  Any help is appreciated!!!

[http://paste.ubuntu.com/765873/](http://paste.ubuntu.com/765873/)

Ideally Windows should be on /dev/sda1. When you reinstalled XP on /dev/sdb1 the MBR was installed to /dev/sda wiping out GRUB. You can reinstall GRUB see **[Reinstalling Grub2 from LiveCD]("http://ubuntuforums.org/showthread.php?t=1195275")**

---

### Post by Bucky Ball on 2011-12-10
Not so fast. You need to run boot-repair from the partition you want booting grub. Download the boot-repair ISO, burn a CD, take out the thumb drive, boot from the CD.

You can also run Ubuntu from a CD then download and run boot-repair (yes, this is possible), with the thumb drive out.

---

### Post by djevans3 on 2011-12-10
I tried running Boot Repair from the CD, and it said it updated correctly.  When I boot, the Grub menu comes up and I can boot into Windows XP fine (minus it corrupted Internet Explorer and Norton Internet Security), however, when I select Ubuntu then it give me:

Error: could not find file
Press any key to continue

Is this still a boot issue or in my install of Ubuntu corrupt?

---

### Post by oldfred on 2011-12-10
Your boot info script showed grub in the MBR of sda & sdb. Which drive are you booting from and have you tried the other drive?

Sometimes this will boot a system that has grub issues. If it boots then you can reinstall grub from the working system.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by djevans3 on 2011-12-10
I'm booting from sda1.  My system is a Dell and the bios doesn't let me specify which SATA drive boots first.  I know there is a boot.ini file on sda3...not sure if windows uses it to boot on sdb1 or not when selected from Grub menu.

---

### Post by Bucky Ball on 2011-12-10
> **djevans3 said:**
> I tried running Boot Repair from the CD, and it said it updated correctly.  When I boot, the Grub menu comes up and I can boot into Windows XP fine (minus it corrupted Internet Explorer and Norton Internet Security) ...

What corrupted them exactly? It is impossible for anything Ubuntu related to effect your Win partition in this way.

---

### Post by djevans3 on 2011-12-11
Internet Explorer was actually just having problems loading the Norton bar add on.  I think Norton was corrupted because it has security implemented to protect the boot sector.  I know there was corruption because CHKDISK found some errors after I ran Boot Repair.

Since Ubuntu is just a toy, I decided to just format the partition and reinstalled Ubuntu.  It boots right up like a champ now.  Lesson learned, Windows can screw anything up :D  Just had to go in and reinstall the programs to my liking.

---

### Post by Bucky Ball on 2011-12-11
Good work! Would you consider your problem solved? If so, please mark the thread solved to help other users. Good luck ... ;)

---

