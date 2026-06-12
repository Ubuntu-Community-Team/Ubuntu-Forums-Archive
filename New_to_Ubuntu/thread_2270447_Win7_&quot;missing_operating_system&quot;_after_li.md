---
title: "Win7 &quot;missing operating system&quot; after live cd catastrophe"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by sunja on 2015-03-23
Hi I need some help getting my win 7 system back in order after the hdd got messed up while playing with an old ubuntu live cd. A few partitions got deleted and the rest were de-windowzed..

using testdisk I managed to recover a deleted partition, sda4, and set the partitions to primary partitions hoping atleast the win7 recover disk would see the install but no. I've rebuilt the mbr with a variety of tools so I'm wondering if thats what got messed up. The hdd is a 120GB SSD. MB is Gigabyte X38-DQ6 if that helps..

[http://paste.ubuntu.com/10658631/](http://paste.ubuntu.com/10658631/) is my latest boot-info txt

So far i get stuck at boot screen with message from boot manager "Missing Operating System", the Win recover/and install CDs do NOT recognize an install so I can't get to the recovery console. I've been doing everything from Ubuntu live cd or a Boot-repair-disk live cd. Boot-Repair cannot seem to fix the boot mgr on sda1.

I'm wondering if i changed the mbr to gpt by mistake and thats what is keeping windows from recognizing win7 on sda2. sda3 is my scratch file partition. sda4 is storage. they mount in Ubuntu and i can view all the files in the file browser. so thats good. everything is there but windows won't acknowledge anything.

thanks!

```
lubuntu@lubuntu:~$ sudo parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  106MB   105MB   ntfs               boot
 2      106MB   32.0GB  31.8GB  ntfs               msftdata
 3      32.0GB  51.9GB  19.9GB  ntfs               msftdata
 4      51.9GB  120GB   68.2GB  ntfs               msftdata

```

```
lubuntu@lubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234439535 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D586EFFE-C906-DA4F-ADF7-BC5BCF5F973E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234439501
Partitions will be aligned on 2048-sector boundaries
Total free space is 4908 sectors (2.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  
   2          206848        62408703   29.7 GiB    0700  
   3        62408704       101316607   18.6 GiB    0700  
   4       101316608       234436607   63.5 GiB    0700 

```

---

### Post by bardo2 on 2015-03-23
hum, that looks strange: Win7 usually uses small 1 partition to get going (i guess, that was sda1). Clues: size 100 MB (typical), first partition (typical)
From first glance, it looks as if you modified something there (EF00 mean EFI-partition IIRC, so Windows seams to have lost its boot procedure. BUT: you may be lucky, the FS is still NTFS, so maybe the data is still there.
Did you install Ubuntu onto NTFS? Which partition? is there a swap partition?
I am wondering of all those NTFS file systems. Doesnt look like 'nix at all.
BTW: EFI hints towards safe-boot BIOS option, which makes the boot process more complicated, because there are more parts involved to get it going properly (BIOS, CMOS, EFI-system, to name a few).
Also the Installation attempt may have changed the data in CMOS (?)
I suggest you get a grasp of how it should be before messing with it further:
[https://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](https://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

Reading through your post once again, i saw you suspect changing to GPT by accident. That could in fact explain parts of it. because the GPT structure could override parts of ... well, but i trust in gdisk to do the right thing, wherever possible.
Still, the partition types from parted and gdisk dont match, so i am wondering, what ubuntu sees and mounts.
Anyway, although i can look into my own computer to see, how a working config looks like, i cannot guide you, since i dont understand, what the situation really is. Further diagnosis is indicated and anyway, i am not a Windows specialist (just know, that bcdedit accesses windows boot datastore).

Hoping for somebody with indepth Windows understanding to take over...

---

### Post by bardo2 on 2015-03-23
Feels a bit like dangerous hazard indeed. When i happen to find myself in such circumstances, i try to calm my nervous system down (a.k.a. time-out) relax, sleep, eat, walk. And come back to it, when a new approach occurred to me. Otherwise, i KNOW, i am able to make the situation even worse out of panic/stress. So my advice would be: The world will still be there tomorrow, give yourself a rest!

---

### Post by oldfred on 2015-03-23
I agree with bardo2's analysis. You must have accidentally changed from MBR to gpt.

Windows only boots with BIOS mode from MBR(msdos) partitioned drives.
Windows only boots with UEFI from gpt(GUID) partitioned drives.

You show BIOS/MBR type Windows partitions which is usually a 100MB NTFS boot partition with boot flag and the main install, or just the main install with all boot files and boot flag.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

And in your sda1 partition you also are missing the BCD.

You need to remove the gpt data and make sure drive is only MBR and then use a Windows repair tool to fix the missing BCD. Boot-Repair can only do minor fixes to Windows, you need a Windows repairCD or flash drive.

      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think fixparts will work, if not:

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

### Post by sunja on 2015-03-23
[QUOTE=bardo2]The world will still be there tomorrow, give yourself a rest![/QUOTE]
hehe yes thats what I've given in to...  all the data is there so I'm not too worried. Its just been a major bother.

I rebuilt the mbr with lilo before going to bed and the "Missing operating system" at boot was replaced by "No partition active". other than that everything is the same, win cd wont recognize the install.

I'll try fixparts to remove GPT and rebuild the mbr. hopefully i'll be back with good news, thanks!

---

### Post by sunja on 2015-03-25
OK! Windows decided to recognize the install. =d> Thanks oldfred!

I ended up using gdisk since fixparts complained about working on a GPT disk for some reason. It was actually pretty simple:

```

**gdisk /dev/sda**
then **r** to get to Recovery/transformation menu
**g** to get to the mbr menu
**p** to view the partition table
**w** to save a new mbr

```

rebooted and Windows recovery recognized the install finally and allowed me to rebuild the disk boot data. 
Everything seems to be back the way it was. Just needed to change one of the drive's letters in windows to what it had been.

Thanks again for your helps! It was a learning experience! :biggrin:

---

### Post by bardo2 on 2015-03-25
Happy to get to know about this relief!

Please use Thread Tools above first post to close thread when/if answered completely.

---

