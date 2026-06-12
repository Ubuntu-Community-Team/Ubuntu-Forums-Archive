---
title: "no such partition. grub rescue -- need to restore regular grub screen"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by necron_99 on 2012-11-20
Hi, the other threads I've seen about this were about deleted partitions. I deleted a partition but I still have active linux And windows partitions. I must have logged into the deleted partition by accident. Is there any way I can get back to the grub screen for my working partitions or do I need to boot from a disk? (I don't have it with me.) Can my working partitions be recovered? Thanks!
PS chainloader gets me "unknown command"

---

### Post by oldfred on 2012-11-21
You can restore grub with an Ubuntu liveCD or boot repair. You may be able to boot manually from grub rescue and then repair grub.

       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    
       [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by necron_99 on 2012-11-22
Thank you!  
ran
boot-info and boot-repair. --attached
recovered windows partition but cannot access grub. How can I get back in?
Thanks again

---

### Post by oldfred on 2012-11-22
Better to post link that Boot-Repair gives you.

You must have deleted the Ubuntu partition. You only show a swap partition and the Windows partitions. But you show some space in the extended partition that is unused. Grub is trying to boot from sda6 and there is no sda6. How did you delete sda6? Ubuntu will not let you delete the partition you are in or did you use Windows. Windows does not 'see' Linux partitions, so it does not handle them correctly.

You may be able to recover your sda6 Linux partition with testdisk from a liveCD. Also gparted or parted see links below. You will probably have to download testdisk into Ubuntu, it is in repository, or many other Linux repairCDs include testdisk.

[https://help.ubuntu.com/community/DataRecovery#Lost](https://help.ubuntu.com/community/DataRecovery#Lost) Partition

       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by necron_99 on 2012-11-22
OK, thanks again. (I know not to expect a reply today and will have to leave off at 3 pm PST myself) 
I have run TestDisk from Windows (7)-- it finds only
dev/sda/ -320GB / 298 / GiB - WDC - WD3200BEVT-22A23T0
Do I need to do the Deeper Search referred to in the TestDisk/Step_By_Step?
How do I access that option? [--edit--I looked at the example again. From this it looks like TestDisk can't find anything more]
Thank you.

---

### Post by necron_99 on 2012-11-22
When I used boot_repair I selected Recommended Repair. I guess I should have chosen my own options.

---

### Post by oldfred on 2012-11-22
Boot repair does not see a Linux partition nor any bootable files, so it only offered to repair the Windows boot.

If testdisk or gparted cannot recover missing partition then the only choice is to reinstall. If you did have unbacked up data, you might recover some with photorec which is really part to testdisk. It is a long slow process and only recovers a file by extension not name as that is gone. (I have used photorec & it does work.)

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by necron_99 on 2012-11-23
Thanks for sticking with this.
I am trying to run gparted but want to be sure of what values to enter. (my winldows partition was 60 of the 320 maybe  i just enter 260--do old deleted partitions affect this?) 

I tried running gpart first:
ubuntu@ubuntu:~$ sudo gpart /dev/sda

*** Fatal error: dev(/dev/sda): seek failure.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ gpart /dev/sda6

*** Fatal error: open(/dev/sda6): No such file or directory
ubuntu@ubuntu:~$ sudo gpart /dev/sda1


Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

<--sda2 , 3 , 5 : same result-->

 sudo gpart /dev/sda4 
 
*** Fatal error: dev(/dev/sda4): seek failure.

---

### Post by oldfred on 2012-11-23
I did not know there was a command gpart????

there is the command line parted and the gui gparted. If launching a gui program from command line you need to use gksudo not sudo, so the graphics are correct.

---

### Post by necron_99 on 2012-11-24
OK thanks. I found gpart on the datarecovery page above -- I guess it is supposed to guess partitions that do not show up. [http://www.brzitwa.de/mb/gpart/](http://www.brzitwa.de/mb/gpart/)
Since it hasn't helped I did try to run gparted--attached is a screenshot. 
I selected Attempt Data Rescue on sda4; it searched and said: No file systems  found on /dev/sda.
After I back up the Windows partition I can attempt the gparted Rescue command, except that I don't know what to enter for start and end blocks. Thanks again.

--edit: Instead of the attachment here are the results of parted print all:
(parted) print all                                                        
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  16.1GB  16.1GB  primary   ntfs         diag
 2      16.1GB  16.2GB  105MB   primary   ntfs         boot
 3      16.2GB  91.5GB  75.3GB  primary   ntfs
 4      91.5GB  320GB   229GB   extended
 5      316GB   320GB   4020MB  logical


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by oldfred on 2012-11-24
The gparted is a quick try. 

When that does not work then try testdisk to see if it can find the missing partition.

---

