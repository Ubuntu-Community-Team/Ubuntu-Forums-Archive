---
title: "Dual Boot Problem: Windows XP will not boot on old Dell laptop"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by andy60 on 2014-08-03
Hello.

   Good afternoon. I installed Ubuntu 14.04.1 as a dual boot setup on my old Dell Inspiron E1705 laptop running Windows XP. Windows XP will not boot, though.
   When I boot, it goes to the menu where I can select Ubuntu, Windows XP, grub, and some other options. If I select Windows XP. Then the screen goes black and jumps back to the same menu screen.
   Ubuntu seems to be running well, other than the fact that 'Suspend' does not seem to work with the computer. I gave the Windows partition 55 GB and the Ubuntu partition 38 GB. I do not know how to use grub. I would appreciate help. Thank you!

Regards,
andy60

---

### Post by sudodus on 2014-08-03
Please post the output of the following command

```
sudo parted -l
``` (space minus ell at the end)

---

### Post by andy60 on 2014-08-03
```
Model: ATA TOSHIBA MK1032GS (scsi)
Disk /dev/sda: 98.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16           diag
 2      49.4MB  55.0GB  55.0GB  primary   ntfs            boot
 4      55.0GB  93.1GB  38.0GB  extended
 5      55.0GB  90.9GB  35.9GB  logical   ext4
 6      90.9GB  93.1GB  2143MB  logical   linux-swap(v1)
 3      93.1GB  98.5GB  5445MB  primary   fat32
```

---

### Post by sudodus on 2014-08-03
The partitions and file systems look good :-)

Is Windows in the original place (or have you moved it from one drive to another, or moved the head of the Windows partition?

How did you shrink the Windows partition?

Can you mount the Windows partition from Ubuntu and read files?

Can you run this command

```
sudo update-grub
```

reboot, and try to boot into Windows again?

---

### Post by andy60 on 2014-08-03
Hello.
   Thanks for your replies! 

> The partitions and file systems look good :smile:
 
   Thanks.

> Is Windows in the original place (or have you moved it from one drive to another, or moved the head of the Windows partition?

   Windows is in the original place as far as I know. I would not know how to move the head of the Windows partion.

> How did you shrink the Windows partition?
 
   I am not sure that I did shrink the Windows partition. There was a slider on the Ubuntu installer that allowed me to pick how much space for the Ubuntu partition and how much to leave for the other operating system. That is all I used to define partitions.

> Can you mount the Windows partition from Ubuntu and read files?

   I was able to see songs in the "My Music" folder from the Windows partition ( "55 GB Volume" ). It shows up as an icon on the tool bar on the right. It appears to mount automatically.

> Can you run this command

 	Code:

 	sudo update-grub 
reboot, and try to boot into Windows again?

  I did that and the results are the same.

I ran the "defragment" Windows utility before installing Ubuntu. I appeciate your help.

Regards,
andy60

---

### Post by andy60 on 2014-08-03
Correction. The toolbar is on the left. Thanks.

Regards,
andy60

---

### Post by sudodus on 2014-08-04
> **andy60 said:**
> Hello.
   Thanks for your replies! 

   Windows is in the original place as far as I know. I would not know how to move the head of the Windows partion.

   I am not sure that I did shrink the Windows partition. There was a slider on the Ubuntu installer that allowed me to pick how much space for the Ubuntu partition and how much to leave for the other operating system. That is all I used to define partitions.

I see. This would probably be OK, unless Windows was hibernated and not shut down properly. But shrinking Windows with Windows tools is recommended, it has higher success rate.
> 
I was able to see songs in the "My Music" folder from the Windows partition ( "55 GB Volume" ). It shows up as an icon on the tool bar on the right. It appears to mount automatically.

Good :-) This means that you are able to ***backup your personal files ***(documents, pictures, mail files, ...) from the Windows partition before doing anything else.
> 
  I did that and the results are the same.

I ran the "defragment" Windows utility before installing Ubuntu. I appeciate your help.

Regards,
andy60

I don't know why you cannot boot Windows. Anyway, before doing anything else you should  ***backup your personal files***, because things may go wrong.

After that I suggest that you download ***Boot Repair***. Do ***not*** use it to repair at once. Use it only to create a ***BootInfo summary*** and post the link to the web page, where it is uploaded. The BootInfo summary will give us more information about what might stop booting Windows. See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andy60 on 2014-08-04
[http://paste.ubuntu.com/7955518/](http://paste.ubuntu.com/7955518/)

Hello.

Here is the link to the Boot Info summary. Thank you!

Regards,
andy60

---

### Post by sudodus on 2014-08-04
I don't understand why you have Plop in the MBR of the internal disk. Have you put it there on purpose or by mistake?

Plop can boot and help boot, but it is unusual to have it in internal disks.

Grub 2 is installed in the Windows Partition. This is even more unusual. Obviously you can boot linux, but not Windows. I don't fully understand if this is a problem or not.

```
=> Plop is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 145505760 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```

***If you have backed up your important data*** (photos, documents etc), I  think it is worthwhile to let Boot Repair try to repair your system.
```
Recommended-Repair
This setting would reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

```

---

### Post by oldfred on 2014-08-04
Grub installed to a NTFS partition is a big issue. We filed bug reports with 10.04 and they supposedly fixed it, but users still can force grub to install to a NTFS partition. That is never right and the NTFS partition will not work.

But NTFS saves a backup boot sector which can easily be restored if backup is valid. Testdisk may say primary is ok as grub in a partition is a valid choice, just not with NTFS.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If backup is invalid, testdisk also can create a new BS, but that is XP type (uses ntldr) and you have to run chkdsk if Vista or later is required (bootmgr).
Or Windows repair CD or flash drive for newer Windows has bootsect.exe to write a totally new BS.

You may need to install a Windows boot loader to MBR to boot Windows and make sure it works correctly as grub really only boots working Windows.
Then install grub to MBR from live installer or Boot-Repair to fix it to boot Ubuntu.

Also note that XP is obsolete and dangerous to use on Internet.

---

### Post by andy60 on 2014-08-04
Good evening.
   Thanks!

> I don't understand why you have Plop in the MBR of the internal disk. Have you put it there on purpose or by mistake?
 I did not put it there. I do not know what Plop or MBR are.

Thanks sudodus and oldfred. I will take your advise into account.

Regards,
andy60

---

### Post by yancek on 2014-08-05
>  I do not know what Plop or MBR are 

Never used Plop myself but I understand it is used to enable booting from flash drives on older computers which don't have that option in the BIOS.

MBR is master boot record, the first sector of the hard drive which contains a small part of the boot code for any operating system which should then point to the partition on which the rest of the boot code/files reside.  Having Grub on an ntfs partition is never a good idea so follow the instructions and links in the post by OldFred.

---

### Post by dave131 on 2014-08-05
In the case of XP, you can use a program called mbrfix - available free-> try downloads.com - to load the bootloader back on your disk.

---

