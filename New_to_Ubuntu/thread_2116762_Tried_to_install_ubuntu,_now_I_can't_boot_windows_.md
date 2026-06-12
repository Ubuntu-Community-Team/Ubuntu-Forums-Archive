---
title: "Tried to install ubuntu, now I can't boot windows 7"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Liutecis on 2013-02-16
Hello everyone,  I think I messed my computer really bad, so I hope to find some answers here. And sorry for my bad english.

I tried to install ubuntu via windows installer. Everything went good for start, but then the installation froze. I didn't know what to do, so I decided that I messed something up and thought that I should delete ubuntu from my windows.  I  uninstalled ubuntu with os-uninstaller. 
Now I can't boot windows 7. I get BOOTMGR is Missing. Tried to reinstall windows, but the installation doesn't see my hard drive. 

I don't know what I did, and don't know how to fix it. Maby someone could help me to fix this?

---

### Post by oldfred on 2013-02-16
Welcome to the forums.

Wubi is just a file inside Windows. You should have just uninstalled it from inside Windows like you would delete any applications.

Not sure what os-uninstalled did. But lets see details of your system.

You will need an Ubuntu liveCD to run this.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
You may be able to repair if you have made the Windows repairCD.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Liutecis on 2013-02-17
Thank you for reply.
Ok, so i did the Boot-info and Boot-Repair.
[http://paste.ubuntu.com/1669894](http://paste.ubuntu.com/1669894)
[http://paste.ubuntu.com/1669897](http://paste.ubuntu.com/1669897)
Also I tried the method from the 3rd link you posted, via Boot-Repair. Didn't help [http://paste.ubuntu.com/1669970](http://paste.ubuntu.com/1669970)

---

### Post by oldfred on 2013-02-17
```
/dev/sda1                  63         2,047         1,985  42 [COLOR=Red]SFS[/COLOR]
 /dev/sda2    *          2,048       206,847       204,800  42[COLOR=Red] SFS[/COLOR]
```
The SFS means you have dynamic disks. 
Which does not work with Linux. I am surprised it installed. It did not used to do that.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by Liutecis on 2013-02-17
It worked! Thank you so much. I converted a dynamic dist to a basic disk with MiniTool Partition Wizzard. The best part is that I haven't lost any files.

---

### Post by oldfred on 2013-02-17
Glad that worked. :)

---

