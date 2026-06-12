---
title: "I broke GRUB"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by spikeyseth on 2012-01-08
I'm trying to uninstall Ubuntu, so i delete the partition its in. however, i now cant load my windows partition because GRUB comes up with:
```
error: unknown filesystem
grub rescue>
```
how can i load my Windows partition and/or remove GRUB?

---

### Post by Maxio142 on 2012-01-08
I found that Ubuntu automatically installs itself into the partition that is already being used, are you sure you didn't delete Windows at the same time?

---

### Post by spikeyseth on 2012-01-08
i have already deleted the ubuntu partition, therefore removing ubuntu. it would seem however that i have also lost my grub config files/folders any help as to how i can bypass grub?

---

### Post by alexandari on 2012-01-08
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Super Grub Disk is your best shot.

**edit later:**  if you say you DON'T have ubuntu anymore on this computer,seems like you have to take a look at this [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/) your windows MBR should be in order,if not,you have to reinstall it too.

---

### Post by oldfred on 2012-01-08
Depending on version of Windows you need to use Windows XP install or Vista/7 repairCD/USB to fix the boot loader.

for XP
fixMBR
for Vista/7
BootRec.exe /fixMBR

Or from Windows 7 repairCd, you can just run the auto fix 3 times.

Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

If you do not have any Windows repair tools, you can install a Windows like bootloader from the Ubuntu liveCD or many Linux repair liveCDs.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

