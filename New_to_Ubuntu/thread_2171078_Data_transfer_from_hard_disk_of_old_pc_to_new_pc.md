---
title: "Data transfer from hard disk of old pc to new pc"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by evilpuppy2 on 2013-08-29
Hi everyone,

I'm not sure that I'm posting this in the appropriate section because I'm new here, so please feel free to point out where this belongs.

I'm a fairly inexperienced Ubuntu user, so please be explicit in your answers :)

I've had Ubuntu 12.04 alongside Windows 7 on my Dell laptop. The laptop stopped working and I was told in the shop that the motherboard failed, but that the hard disk was ok.

I have put the disk into an enclosure which I can connect to my new pc (hp Pavilion, Windows 8) via two USB ports, and this allows me to see my files from the Windows side of my old computer. However I am not able to see any data from the Ubuntu side, and that's the only really important stuff!

What exactly does one do in such a situation? Is it normal that I can't see the Ubuntu data, because the instructions for the hard disk enclosure do mention only that it works with Windows and Mac?

I've been looking for the solution online, but am finding it difficult, probably because I just don't know the correct technical terms to search for and I am quite desperate by now as I really need my data back urgently.

---

### Post by coldraven on 2013-08-29
Windows will not read your Ubuntu disk you will have to boot a Live CD or USB stick to copy them over.
If you still have you could use your original Ubuntu installation disk or download a newer version (12.04)
You can use Unetbooting to create a bootable USB stick from the Ubuntu .iso file. There is a Windows version.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

The problem will be in getting your Win8 machine to boot with the USB stick that you have created.
 I guess that you will have to disable Secure Boot in the BIOS. You need to Google that, I do not have any Windows PCs.

Once booted into the Live Ubuntu session, plug in your enclosure and you should be able to copy the files. to your hard drive.
It might be safer to copy the files to another memory stick and then when you are back in Windows to copy them again.
This avoids the problem of Windows suddenly discovering a new folder on it's drive that it did not create itself.
The additional memory stick will be formatted in FAT32 which Windows will be happy with.

So you would need four spare USB ports.
One for the Ubuntu stick that you created with Unetbootin
Two for your enclosure
One for the FAT32 stick to use as a destination for your files (or use a SD card if you have a card reader)

I hope that makes sense, I just woke up :)

---

### Post by evilpuppy2 on 2013-08-29
Thanks for the reply!

Unfortunately I'm not sure I understand what a live CD is...

Nevertheless, I did think that the problem might be Windows, so I installed Ubuntu 12.04 on my new computer as well. However, whether in Ubuntu or Windows, the new computer only seems to see the windows part of the old disk and not the Ubuntu part. Does that sound normal to you?

---

### Post by mörgæs on 2013-08-29
> **evilpuppy2 said:**
> 
I'm not sure that I'm posting this in the appropriate section because I'm new here, so please feel free to point out where this belongs.

I'm a fairly inexperienced Ubuntu user, so please be explicit in your answers :)



Welcome to the fora. I guess Absolute Beginners Section will be the best place for the thread, so moved.

---

### Post by eternal243 on 2013-08-29
> **evilpuppy2 said:**
> Thanks for the reply!

Unfortunately I'm not sure I understand what a live CD is...

Nevertheless, I did think that the problem might be Windows, so I installed Ubuntu 12.04 on my new computer as well. However, whether in Ubuntu or Windows, the new computer only seems to see the windows part of the old disk and not the Ubuntu part. Does that sound normal to you?

Hello there evilpuppy2 and welcome the forums!

A Live CD is usually the same as an installations cd downloaded from ubuntu.com. It means that you can run Ubuntu in live mode, from your RAM without having to install it, it is very handy for troubleshooting or if you just want to try out Ubuntu on a new PC to see if the hardware is compatible.

Don't trouble yourself with a live cd now, since you have installed Ubuntu and it seems to be working, so let us continue to troubleshooting your harddrive.

The reason windows can't see your harddrive is probably because your linux-partitions is using a filesystem not supported by microsoft. Probably ext2, ext3 or ext4. This means you will need a linux installation to see those partitions. Please open Terminal in Ubuntu and type in the following command.

```
sudo fdisk -l
```

This is a command that list all harddrives connected to your computer and all partitions on those harddrives. Then select the text, copy it and post it back here. :)

**EDIT: ** also run this command and post the output, it will help us to know what USB devices are connected to your pc.

```
lsusb
```

---

### Post by evilpuppy2 on 2013-08-29
> **eternal243 said:**
> Hello there evilpuppy2 and welcome the forums!

A Live CD is usually the same as an installations cd downloaded from ubuntu.com. It means that you can run Ubuntu in live mode, from your RAM without having to install it, it is very handy for troubleshooting or if you just want to try out Ubuntu on a new PC to see if the hardware is compatible.



Thank you for the welcome and the clear explanation! :D

The command sudo fdisk -l gives the following output:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xebd4268b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x259d4594

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       81920     1617919      768000    7  HPFS/NTFS/exFAT
/dev/sdb3         1617920   298096727   148239404    7  HPFS/NTFS/exFAT
/dev/sdb4       298098686   488396799    95149057    5  Extended
/dev/sdb5       298098688   480290815    91096064   83  Linux
/dev/sdb6       480292864   488396799     4051968   82  Linux swap / Solaris


The command lsusb gives this:

Bus 002 Device 002: ID 0bda:571c Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

---

### Post by eternal243 on 2013-08-29
> **evilpuppy2 said:**
> Thank you for the welcome and the clear explanation! :D

The command sudo fdisk -l gives the following output:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xebd4268b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x259d4594

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       81920     1617919      768000    7  HPFS/NTFS/exFAT
/dev/sdb3         1617920   298096727   148239404    7  HPFS/NTFS/exFAT
/dev/sdb4       298098686   488396799    95149057    5  Extended
/dev/sdb5       298098688   480290815    91096064   83  Linux
/dev/sdb6       480292864   488396799     4051968   82  Linux swap / Solaris
```


The command lsusb gives this:

```
Bus 002 Device 002: ID 0bda:571c Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

Okay, this tells me that Ubuntu recognizes two physical harddrives, one that is 1000gb and one that is 250gb. The first drive has 2 messages that troubles me. The first one is as follows:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
```

And this is the second message.
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

Haven't seen those messages before, maybe someone else can help out here, I will try to do some google research to see what the problem might be.

---

### Post by eternal243 on 2013-08-29
Okay, the GPT warning can probably be ignored. I found this on wikipedia.

> Some distribution tools, have limited or no support. util-linux' fdisk, recognises a GPT being present but cannot use or modifiy it.[citation needed] GNU fdisk (at least until version 1.2.5) cannot even recognise GPTs and may seriously damage them.[citation needed]

New tools such as gdisk,[10] GNU Parted,[11][12] Syslinux, grub 0.96+patches and grub2 have been GPT-enabled.

**Quoted from: [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)**

---

### Post by oldfred on 2013-08-29
Fdisk does not support gpt partitioned drives and all Windows 8 pre-installed systems use gpt partitioning. Actually they just released a new fdisk, but it will be a while before that is in anything.
You can use parted, gparted, or gdisk which is in the repository and the fdisk for gpt drives to see gpt drives. 

Since fdisk did show Linux partition on old drive, it may just be a permissions and ownership issue. If you are not the same user you do not have default permissions to see or use the data. But as administrator with sudo you should be able to.

Try this but you have to be extremely careful not to delete or move any system info. You can damage system as you have total access. Just use it to copy your data. lFrom command line launch nautilus in administrative mode.

sudo nautilus

If copying to Windows make sure it is not hibernated. And really better to copy to another NTFS data partition not the main system partition as Windows may eventually get corrupted. From Linux the NTFS driver exposes all the normally hidden Windows system files & folders and accidentally moving something will corrupt system. Just with XP I used to always turn on the view of all files and would accidentally move a system file and corrupt it. Hard way to learn how to fix it. :)

---

### Post by whitesmith on 2013-08-29
> **eternal243 said:**
> Okay, this tells me that Ubuntu recognizes two physical harddrives, one that is 1000gb and one that is 250gb. The first drive has 2 messages that troubles me. The first one is as follows:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
```

And this is the second message.
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

Haven't seen those messages before, maybe someone else can help out here, I will try to do some google research to see what the problem might be.

I had a similar problem with a windows-formatted hd. [http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd]("http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd") is the method i used to convert to mbr, which is linux-readable. I would strongly suggest using a tool like **clonezilla** to first image the old drive, although i'm not sure if that product works across usb. Looks like empiricism will rule the day. These are powerful tools that should be used with caution.

---

### Post by oldfred on 2013-08-29
Windows 8 boots in UEFI mode and will only boot in UEFI mode from gpt partitioned drives.

Only if you want a BIOS install of older Windows, then may you want to remove gpt partitioning. But that is a totally separate licensed copy of Windows than the pre-installed version.

Ubuntu will boot in either BIOS or UEFI from a gpt partitioned drive.

---

### Post by evilpuppy2 on 2013-08-30
> **oldfred said:**
> Fdisk does not support gpt partitioned drives and all Windows 8 pre-installed systems use gpt partitioning. Actually they just released a new fdisk, but it will be a while before that is in anything.
You can use parted, gparted, or gdisk which is in the repository and the fdisk for gpt drives to see gpt drives. 

Since fdisk did show Linux partition on old drive, it may just be a permissions and ownership issue. If you are not the same user you do not have default permissions to see or use the data. But as administrator with sudo you should be able to.

Try this but you have to be extremely careful not to delete or move any system info. You can damage system as you have total access. Just use it to copy your data. lFrom command line launch nautilus in administrative mode.

sudo nautilus

If copying to Windows make sure it is not hibernated. And really better to copy to another NTFS data partition not the main system partition as Windows may eventually get corrupted. From Linux the NTFS driver exposes all the normally hidden Windows system files & folders and accidentally moving something will corrupt system. Just with XP I used to always turn on the view of all files and would accidentally move a system file and corrupt it. Hard way to learn how to fix it. :)

Unfortunately all the new suggestions relating to fdisk and gpt are a bit too technical for me to understand.
Could you give a detailed step-by-step procedure for checking whether it's an ownership issue?

Also, am I to understand that if I connect the enclosure to a computer with windows 7, I should be able to see the Ubuntu data on the disk?

---

### Post by mastablasta on 2013-08-30
windows can't read data on ubuntu partition. however if you can boot into linux from your computer (live) youc an move that data to NTFS and then windows cna read it.

there are a couple of 3rd party tools thta can read linux partition directly from windows. i am not sure how well they work and if the work in win8 and 7 but:
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
a few more can be found here: 
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

as long as data on ubuntu part of that disk is not encrypted it should be readable. i am not sure fi you can write to that part of disk from window sbut if oyu can read it you can move the data arround.

by default windows can read&write FAT, FAT32, NTFS
Linux can also read6 write on those types but can not really install to them (well ti can but it's a mess). linux uses other file systems such as Ext3, Ext4 (default in Ubuntu is ext4), NFS, ZFS and others. none of these filesystems can be read by windows without additional tools.

---

### Post by oldfred on 2013-08-30
MBR and gpt are how the drives are partitioned. 
You then format the partitions with file structures like NTFS for Windows or ext4 for Linux.
Then the files & folders withing the formatted partitions are given ownership & permissions for users to access the files. 
But if reading from a different system the ownership will not auto transfer. You have to reset that or override with sudo or Superuser rights.

sudo Nautilus should then let you copy files, just becareful not to delete anything or move system files.

---

