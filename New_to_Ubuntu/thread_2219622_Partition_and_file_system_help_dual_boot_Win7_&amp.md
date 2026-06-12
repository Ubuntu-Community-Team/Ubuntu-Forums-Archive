---
title: "Partition and file system help dual boot Win7 &amp; Xubuntu14.04 upgrade to all Xubuntu"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by Brother_Dave on 2014-04-24
I have two hard disk drives with Windows 7 64 bit and Xubuntu 14.04 beta 2 as a dual boot.  I then ran an upgrade in Xubuntu so I might already be 14.04LTS not sure.

I ordered a new 16GB USB flash drive with Xubuntu 14.04LTS on it due tomorrow. Then I want to  partition my two hard drives for only Linux and keep my NTFS Win 7 data to use in Linux.

In Win 7, my Disks & partition info is
```

WD5000 465 GB   ATA bus   
   C:  NTFS  128 GB capacity 49 GB used   System (WIN7)    Primary 
   E:  NTFS  169 GB      "      < 1 GB used    (my data 1)         Logical
   F:  NTFS   169 GB     "       40 GB used     (my data 2)        Logical

Maxtor 5A25030 234 GB  ATA bus
   D: NTFS   140 GB capacity   111 GB used (my data 3)       Primary
 (Linux) ext4  91 GB     "                  ?                  ?                Logical
(Linux) ext4   2.5 GB   "                  ?                  ?                Logical

In the Linux OS, I ran Terminal

$ sudo fdisk -l      and have this info:


Disk /dev/sda: 500.1 GB, 500103634432 bytes
240 heads, 63 sectors/track, 64600 cylinders, total 976764911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End          Blocks          Id         System
/dev/sda1   *               63   268410239   134205088+   7  HPFS/NTFS/exFAT
/dev/sda2       268410240   976751999   354170880     f   W95 Ext'd (LBA)
/dev/sda5       268410303   622581119   177085408+   7  HPFS/NTFS/exFAT
/dev/sda6       622581183   976751999   177085408+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3be370b3

   Device Boot        Start         End         Blocks       Id     System
/dev/sdb1                2048   294617013   147307483    7    HPFS/NTFS/exFAT
/dev/sdb2       294617086   490233855    97808385    5     Extended
/dev/sdb5       294617088   484995071    95188992   83     Linux
/dev/sdb6       484997120   490233855     2618368   82     Linux swap / Solaris
dave@dave-GA-MA785GM-US2H:~$ 
```
              (Gigabyte Motherboard  AMD Sempron dual core )

Should I just use the flash drive to install the latest Xubuntu 14.04 LTS ?  Please tell me how to best custon partition from there, or should I gparted first? and how?

Linux newbie. Thanks !

---

### Post by oldfred on 2014-04-24
I would still fully backup Windows. We see many users come back with one application or game that just does not run as well in Linux or the equivalent is not as good.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

You can partition anyway you want. But if you have updated you beta install, it is just the same as the final version. It just may have larger log files & histories that you still could houseclean out.

If you are going to keep NTFS partition you must have a Windows repairCD or flash drive to run chkdsk occasionally. You cannot run chkdsk from Linux.  And Ubuntu runs fsck on your / partition every 40 reboots.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

When you have larger data partitions I prefer to use smaller / (root) of 20 or 25GB.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Brother_Dave on 2014-04-25
Thank you for all that specific information. Much appreciated.  When I do this in 2-3 more days, I'll come back here with possibly some new questions. Reluctantly, I'll have to keep Windows 7 as a dual boot until Skype  and Google Drive using Grive work well.

---

### Post by Brother_Dave on 2014-04-28
I received the new 16 GB flash drive with Xubuntu 14.04LTS installed. Problem is that that the bootloader GRUB 2.02 is still corrupt; and I can not boot from USB or a DVD in my optical drive.  "Grub Rescue > still comes up. 

So, running in Xubuntu I downloaded and installed OK a boot-repair program for AMD 64 bit, ran it OK. BUT the same problem remains.

Here is the report generated.   [http://paste.ubuntu.com/7354996/](http://paste.ubuntu.com/7354996/)      (Yes my 14.04 beta 2 did upgrade to LTS before the new flash drive arrived)

Please look at that, and tell me what to do next.  Thanks for your help !

I also have decided to remove WIN 7, reinstall WIN XP-pro Final, and then keep a dual boot Linux & XP for awhile longer before going all Linux desktop and an Acer C720 Chromebook.

---

### Post by oldfred on 2014-04-28
Since you have two drives, you should install the Windows boot loader back onto the Windows drive. 
I do not like the autofix where Boot-Repair auto installs grub to the MBR of every drive. You want the Windows boot loader on sda, and grub in the MBR on sdb.
You can use Boot-Repair to install a Windows type boot loader to sda. In advanced choose Windows and drive that is sda for boot loader. Or you can use your Windows repair CD or flash drive to run the fix MBR command.

A few BIOS will not let you boot unless you have a boot flag on a primary partition. You show no boot flag on sdb drive. Grub does not use boot flag, but since some BIOS need one just to let you start to boot, then you should have one. You can put it on sdb1 with gparted.

You show a 64 bit capable cpu, did you install the 32 bit or 64 bit version of Ubuntu?
And it looks like the Radeon card is an older model. I have nVidia so have not tracked those as much.
       This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Not sure you should have XP, but be sure to not use IE as that has a new unfixed bug.

I do not see anything else, except perhaps the far into drive message.
But what mode is drive set to. New systems should have drive as AHCI not IDE. Or LBA or large.
But AHCI may not work with XP, newer Windows have drivers.

Some BIOS will not boot unless all boot files are fully within the first 100MB of a drive. Could be BIOS, IDE setting or grub, but it only applies to some systems and more to external drives than internal
If that is the case you need either a /boot or a smaller / (root) fully inside the first 100GB of drive with rest of the drive as /home or data. But you currently have a large NTFS partition at the beginning of sdb.

---

### Post by Brother_Dave on 2014-04-29
Thanks oldfred for the suggestions which I will try later.

Another thing I noticed yesterday is the boot.repair data log suggested that I make the 250GB MAXTOR D: drive with Linux & WIN 7 partitions the primary boot drive and not the C: Western Digital 500GB drive now having only only windows 7 and NTFS.   When I go into the BIOS the first time, only the 500GB C: Windows drive shows ! Nowhere in the BIOS can I get the Linux D: E: F: drive 2 to show up. However, every time I exit BIOS setup without making any changes, both HD Drives are properly listed; also then Grub loader shows the four choices of Xubuntu 14.04 and 2 memory tests and Windows 7 and all work. Since I have all my data backed up in many places locally and web and cloud, I can re-partition, format, etc. either HDD if that would be easier.  Maybe I should install Linux only on the 500GB main drive that shows up always in the BIOS ?   Right now, I can not boot from USB-flash nor from CD/DVD optical drive.

---

### Post by oldfred on 2014-04-29
Grub does not use boot flag. But some BIOS require a boot flag on a primary partition to even let you start to boot. So Boot-Repair suggests a boot flag. That does not make it bootable.
The boot flag is used by Windows to know which partition has the Windows boot files. And BIOS determines which drive is the boot able drive for all systems. And code in MBR then determines what will boot.

BIOS should show both drives, but some BIOS only boot from the first drive. Or you may have an old IDE/PATA system and not configured cable select correctly?
Really old systems only booted from primary master, other drive was just a slave or data drive.

---

### Post by Brother_Dave on 2014-05-05
When I re-installed from a commercial OSDisc  Xubuntu 14.04LTS,  I moved the Grub bootloader from sdb to sda HD drive and all works as before. I still have to go into BIOS and exit without saving to have both HD drives show in BIOS and have Grub choices appear normally. I'll work on that hardware or BIOS settings problem later. Since I like Linux much better than Windows, I will likely just run 14.04.  

In re-installing my older Win Xp-pro OS o replace my Win 7  OS on C:  or sda drive, it formatted or changed my E; and F: (for some data backup only) logical partitions which were maybe sda3  and sda4. So here is what I now have:   

                                                     Disk /dev/sda: 500.1 GB, 500103634432 bytes            
            240 heads, 63 sectors/track, 64600 cylinders, total 976764911 sectors            
            Units = sectors of 1 * 512 = 512 bytes            
            Sector size (logical/physical): 512 bytes / 512 bytes            
            I/O size (minimum/optimal): 512 bytes / 512 bytes            
            Disk identifier: 0x00000001            
                           Device Boot      Start         End      Blocks   Id  System            
            /dev/sda1   *          63   268410239   134205088+   7  HPFS/NTFS/exFAT            
            /dev/sda2       268410240   976751999   354170880    f  W95 Ext'd (LBA)            
            /dev/sda5       268410303   622581119   177085408+   7  HPFS/NTFS/exFAT            
            /dev/sda6       622581183   976751999   177085408+   7  HPFS/NTFS/exFAT            
                        Disk /dev/sdb: 251.0 GB, 251000193024 bytes            
            255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors            
            Units = sectors of 1 * 512 = 512 bytes            
            Sector size (logical/physical): 512 bytes / 512 bytes            
            I/O size (minimum/optimal): 512 bytes / 512 bytes            
            Disk identifier: 0x3be370b3            
                           Device Boot      Start         End      Blocks   Id  System            
            /dev/sdb1            2048   294617013   147307483    7  HPFS/NTFS/exFAT            
            /dev/sdb2       294617086   490233855    97808385    5  Extended            
            /dev/sdb5       294617088   484995071    95188992   83  Linux            
            /dev/sdb6       484997120   490233855     2618368   82  Linux swap / Solaris            
            dave@dave-GA-MA785GM-US2H:~$   

Would it be better to use Gparted or some graphical partition software to put all of /dev/sdb  on /dev/sda and format sdb for backup ? Not sure if my older NTFS filesystem needs to be changed for linux?

Thanks for your help !

---

### Post by oldfred on 2014-05-05
Windows can do nasty things to partition tables. It does not correctly see Linux partitions and often forgets to include them when rewriting partition tables.

I would not run XP any more except if not at all connected to Internet.

Not sure how you want to re-arrange installs?
But I prefer to have Windows on one drive and Ubuntu on the other. But if you cannot boot from both drives because of a very old BIOS then you have to have grub2's boot loader in sda. Generally Windows likes to be first partition on the drive set as Boot in BIOS, but only has to be on a primary partition to boot from.

---

### Post by Brother_Dave on 2014-05-07
New problem of Win 7 re-install wiping out GRUB to run 14.04. I'll make a new post with correct subject.

---

