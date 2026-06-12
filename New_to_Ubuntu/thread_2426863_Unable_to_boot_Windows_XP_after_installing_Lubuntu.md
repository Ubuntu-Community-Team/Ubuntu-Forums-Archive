---
title: "Unable to boot Windows XP after installing Lubuntu in dual boot"
date: 2019-09-14
forum: New to Ubuntu
---

### Post by mydomdom on 2019-09-14
Hello,
I installed Lubuntu (on an Acer One Aspire) in dual boot with Windows XP.
Using a live-usb:
- I first shrinked the NTFS partition (from 150 Go to around 110Go)
- then I created an ext4 partition / for Lubuntu (20Go)
- then I created an ext4 partition /home for Documents (20Go)
- I let the 8 Go NTFS partition to restore Windows as it was.
The computer boots with Lubuntu: no problem. 
But it doesn't boot on Windows XP, although it is proposed in the Grub screen.

I ran Boot-repair without success.
I did not dare to tick-mark "Restore MBR" when using boot-repair.

```
dom@dom-AO751h:~$ sudo fdisk -lDisque /dev/sda : 149,1 GiB, 160041885696 octets, 312581808 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Type d'étiquette de disque : dos
Identifiant de disque : 0xc00b7e20


Périphérique Amorçage     Début       Fin  Secteurs Taille Id Type
/dev/sda1                  2048  16779263  16777216     8G  2 root XENIX
/dev/sda2    *         16779264 231623013 214843750 102,5G  7 HPFS/NTFS/exFAT
/dev/sda3             231624704 270686207  39061504  18,6G 83 Linux
/dev/sda4             270686208 307795967  37109760  17,7G 83 Linux
dom@dom-AO751h:~$ sudo parted  -l
Modèle: ATA Hitachi HTS54321 (scsi)
Disque /dev/sda : 160GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos
Disk Flags: 


Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      1049kB  8591MB  8590MB  primary  ntfs
 2      8591MB  119GB   110GB   primary  ntfs                 démarrage
 3      119GB   139GB   20,0GB  primary  ext4
 4      139GB   158GB   19,0GB  primary  ext4



```
Attached is the Bootinfo report.

If possible, my priority is to be able to retrieve my data on the NTFS partition.
Then to get Windows XP and Lubuntu on this pc...
Thank you in advance for your kind help
Dom

---

### Post by yancek on 2019-09-14
In order to get help, you will need to actually post the link you got when you ran boot repair.  What exactly happens when you select the xp option in Grub?

---

### Post by mydomdom on 2019-09-15
Hello, Thanks for helping.
The BootInfoRepair report can be seen there: [https://pastebin.com/CNVBFtdv](https://pastebin.com/CNVBFtdv)
> [COLOR=#000000]What exactly happens when you select the xp option in Grub?[/COLOR]
The Grub screen disappears for 2 or 3 seconds (only a prompt "_" can be seen) then it reappears. Win XP is not launched

Please note also that I can launch without problems the "Windows recovery environment (on /dev/sda2)" from the Grub

---

### Post by yancek on 2019-09-15
You have the Ubuntu Grub boot code installed in the MBR of the drive and have Grub boot files on the Ubuntu partition (sda3) which is correct.  I expect the reason you cannot boot XP is because you have installed Grub boot files on the XP partition (sda2).  This is something that should not be done and will not happen without user intervention.  Never install Linux boot code to a windows partition.  I expect you will need the XP install CD to repair this and if you don't have that, do an online search to find some software to repair the windows boot files.  Likely will need to re-install boot code to the windows partition and MBR.  You won't be able to boot Lubuntu from XP after this although that is possible through a convoluted process.  Probably the simplest thing to do after repairing the windows boot is to re-install Lubuntu and make certain the boot code is installed to the MBR and not on any ntfs partition.

Recovering data from the windows partition can be done by simply mounting that partition (sda2) from within Lubuntu.  Lots of tutorials and sites on mounting windows from Lubuntu/Ubuntu are available online.

---

### Post by oldfred on 2019-09-15
You never install grub to a NTFS partition, and almost never to a partition. You always want to specify a drive like sda, not a partition like sda2 for where to install grub.

NTFS has vital Windows info in the partition boot sector. But it does keep a backup and if you only installed grub once to the sda2's PBR or BS - partition boot sector. And testdisk can restore that backup. Testdisk also has tools to create a new BS, but that is XP type and chkdsk normally required afterwards. Since you have XP it may just work.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by mydomdom on 2019-09-16
Yancek and Oldfred, thank you so much for your help !

Just for info, I really don't think I deliberatly installed Grub to the windows partition !
I used the Live-usb:
- selecting Install Lubuntu, 
- then resizing the NTFS partition (from 150Go to 110Go), 
- then creating 2 ext4 partitions (/ and /home)
- and finally selecting the / partition (as far as I remember) to install Lubuntu.
As far as I remember, I never selected the NTFS partition to install GRUB. BTW, I don't remember having to do anything to install Grub...
But, I may make a mistake... ;) since I'm here asking for help !

I'm going to first save my data (I can access to them), then repair the windows boot as you suggest. 
I already saw Testdisk before posting, so I'm not surprised by your suggestion OldFred.
I'll give you an update when all this is done (not before Wednesday since I'm quite busy).

Last thing: do you have a link with a good tutorial so that (when I repair the errors) I can reinstall Lubuntu in dual boot with Windows XP without putting the mess in the systems ?;)
Thank you !
Dom

---

### Post by oldfred on 2019-09-16
You should just be able to use the Something Else install option.
And you can choose to reuse your exiting partition(s). If you have separate /home partition be sure NOT to check the format box. But you need to always have good backups anyway.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

