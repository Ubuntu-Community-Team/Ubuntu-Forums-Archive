---
title: "Windows 7 doesn't start after ubuntu installation"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by rumpels110 on 2012-09-06
Hi all,

I am in big trouble since I tried to replace my XP installation by ubuntu:

I  have a single hdd with a primary and two logical partitions. Primary  was xp, first logical is windows 7, second data, both ntfs.
Since I  installed ubuntu, windows 7 is shown under media/win7 but unbootable.  Tried to handle that with boot-repair. It shows win7 under  "further  options" - > "mark this as boot" ... "sda5: win"
When I try to repair by Windows 7 install CD, it is not shown in the list of exisiting operating systems.
What happens?

already tried "grub-update", doesn't work...

sudo fdisk -l
/dev/sda1   *           63    41945714    20972826   83  Linux
/dev/sda2        41945776   488375999   223215112    f  W95 Erw. (LBA)
/dev/sda5       41945778   104856254    31455238+   7  HPFS/NTFS/exFAT
/dev/sda6       104856318   488375999   191759841    7  HPFS/NTFS/exFAT

please help ... any ideas??

---

### Post by critin on 2012-09-06
Doesn't Windows have to be Primary?

I know linux can be logical or primary, but I didn't think windows could.

---

### Post by rumpels110 on 2012-09-06
It worked well with these settings, yes... 
but it seems to be uncoverable at this time. This is really bad :/

---

### Post by coffeecat on 2012-09-06
> **rumpels110 said:**
> 
I  have a single hdd with a primary and two logical partitions. Primary  was xp, first logical is windows 7, second data, both ntfs.

A Windows C: partition can be on a logical partition, but it cannot boot from a logical partition. When you installed Windows 7 to a logical partition, the installer would have detected XP on a primary and installed the Windows 7 boot files to that partition. The Windows 7 installer tends to do that anyway if it sees an XP installation. Now that you have overwritten the XP partition, Windows 7 has lost its boot files and that is why update-grub doesn't see it either.

First thing you need to do is to create a primary NTFS partition for the boot files. But how you recreate the Windows 7 boot files in that partition from the installer DVD, I don't know. I'm sure it's possible and perhaps someone who has been through this will post.

---

### Post by rumpels110 on 2012-09-06
This sounds really bad :/. Is there any way to cope with that problem, please help if you have an idea...

---

### Post by rumpels110 on 2012-09-06
What about this: 

1) backup partition via boot-cd
2) reinstall win7 on logical
3) backup mbr
4) restore partition
5) restore mbr

^ would this work?

---

### Post by Mark Phelps on 2012-09-06
Basically, No.  Win7, when installed to an existing partition, without any other Windows install on the drive, must be to a Primary partition -- because it will try to write the boot files there.

Rather than reinstalling Win7, which will start you all over from the beginning, you should check out Minitool Partition Wizard FAW at their site.  I know the paid version has an option to convert Logical to Primary, but don't know if the free version does.

Once you convert the Win7 partition to Primary, then you should be able to repair it with boot-repair as it now has somewhere to write the boot files.

---

### Post by rumpels110 on 2012-09-06
This sounds cool :D, but is there a comparable tool for linux? As I've told, I am unable to access my Win7 OS. I would need a linux solution instead ...

goddamn ... complicated

| Update:

I realized, that there is an ability to download a free bootable CD. In the screenshots I can see, that there is an option to set a partition as primary! I'am going to make a fresh backup of my data and try to do this. Thanks a lot, I will report immediately...

---

### Post by coffeecat on 2012-09-06
> **rumpels110 said:**
> 
^ would this work?

No. As I've already said, and as Mark Phelps has just explained, the Windows boot files must be on a primary partition. We are not talking about the mbr here, but the partition boot sector. 

Taking up Mark Phelps idea of converting the Windows 7 logical partition into a primary one, there is a free utility that can do this. See here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts is a command line only utility with both Linux and Windows versions. In theory, you could run the Linux version in Ubuntu and convert the Windows partition to a primary one. But I have no experience of doing this with Windows and cannot say whether this would be a good idea or not.

---

### Post by jerome1232 on 2012-09-06
> **coffeecat said:**
> No. As I've already said, and as Mark Phelps has just explained, the Windows boot files must be on a primary partition. We are not talking about the mbr here, but the partition boot sector. 

Taking up Mark Phelps idea of converting the Windows 7 logical partition into a primary one, there is a free utility that can do this. See here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts is a command line only utility with both Linux and Windows versions. In theory, you could run the Linux version in Ubuntu and convert the Windows partition to a primary one. But I have no experience of doing this with Windows and cannot say whether this would be a good idea or not.

I have done the opposite successfully (moved Windows primary c: partition to a logical partition, boot files were already on their own primary partition) successfully. I wouldn't recommend trying it unless your private data is backed up somewhere safe. It was scary that first boot, it all worked out though.

---

### Post by rumpels110 on 2012-09-07
Hi all, 

promised to report. I successfuly changed the type from logical to primary. Windows is detected in the recovery console, but cannot be repaired.
Its so confusing. Boot-Repair finds the partition and identifies it as win7. but it is not shown in the drop down.

I started the bootinfoscript, and this is the outcome:

```

[LIST=1]
[*]   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]
[*] 
[*] 
[*]============================= Boot Info Summary: ===============================
[*] 
[*] => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
[*]    the same hard drive for core.img. core.img is at this location and looks 
[*]    for (,msdos1)/boot/grub on this drive.
[*] 
[*]sda1: __________________________________________________________________________
[*] 
[*]    File system:       ext4
[*]    Boot sector type:  Grub2 (v1.99)
[*]    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
[*]                       and looks at sector 17047095 of the same hard drive 
[*]                       for core.img, but core.img can not be found at this 
[*]                       location.
[*]    Operating System:  Ubuntu 12.04.1 LTS
[*]    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
[*] 
[*]sda2: __________________________________________________________________________
[*] 
[*]    File system:       ntfs
[*]    Boot sector type:  Windows Vista/7: NTFS
[*]    Boot sector info:  According to the info in the boot sector, sda2 starts 
[*]                       at sector 63. But according to the info from fdisk, 
[*]                       sda2 starts at sector 41945778.
[*]    Operating System:  Windows 7
[*]    Boot files:        /Boot/BCD /Windows/System32/winload.exe
[*] 
[*]sda3: __________________________________________________________________________
[*] 
[*]    File system:       Extended Partition
[*]    Boot sector type:  Unknown
[*]    Boot sector info: 
[*] 
[*]sda5: __________________________________________________________________________
[*] 
[*]    File system:       ntfs
[*]    Boot sector type:  Windows XP: NTFS
[*]    Boot sector info:  According to the info in the boot sector, sda5 starts 
[*]                       at sector 63.
[*]    Operating System:  
[*]    Boot files:        
[*] 
[*]============================ Drive/Partition Info: =============================
[*] 
[*]Drive: sda _____________________________________________________________________
[*] 
[*]Disk /dev/sda: 250.1 GB, 250059350016 bytes
[*]255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
[*]Units = sectors of 1 * 512 = 512 bytes
[*]Sector size (logical/physical): 512 bytes / 512 bytes
[*] 
[*]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
[*] 
[*]/dev/sda1                  63    41,945,714    41,945,652  83 Linux
[*]/dev/sda2    *     41,945,778   104,856,254    62,910,477   7 NTFS / exFAT / HPFS
[*]/dev/sda3         104,856,255   488,375,999   383,519,745   f W95 Extended (LBA)
[*]/dev/sda5         104,856,318   488,375,999   383,519,682   7 NTFS / exFAT / HPFS
[*] 
[*] 
[*]"blkid" output: ________________________________________________________________
[*] 
[*]Device           UUID                                   TYPE       LABEL
[*] 
[*]/dev/loop0                                              squashfs   
[*]/dev/sda1        8c57a0c1-60de-44f9-b976-5c66a1e1bbdb   ext4       
[*]/dev/sda2        B0C81411C813D486                       ntfs       WIN7
[*]/dev/sda5        243850F93850CB84                       ntfs       BigStorage
[*]/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386
[*] 
[*]================================ Mount points: =================================
[*] 
[*]Device           Mount_Point              Type       Options
[*] 
[*]/dev/loop0       /rofs                    squashfs   (ro,noatime)
[*]/dev/sr0         /cdrom                   iso9660    (ro,noatime)
[/LIST]


```

If you have any kind of idea how to repair this boot system in a way that I am able to run windows 7 again, it would help me so much!

Thanks a lot for each kind of idea

---

### Post by coffeecat on 2012-09-07
> **rumpels110 said:**
> 
[list][*]sda2:
[*]    File system:       ntfs
[*]    Boot sector type:  Windows Vista/7: NTFS
[*]    Boot sector info:  According to the info in the boot sector, sda2 starts 
[*]                       at sector 63. But according to the info from fdisk, 
[*]                       sda2 starts at sector 41945778.
[*]    Operating System:  Windows 7
[*]    Boot files:        /Boot/BCD /Windows/System32/winload.exe
[*] [/list]

You are missing /bootmgr from the boot files, but I wonder if the reason the Windows recovery console can't/won't repair your installation is because of the boot sector discrepancies in that partition. What you see there is usual if Windows is in one partition with the boot files in another, as you had it before. Your ex-WindowsXP partition would have had a start sector of 63, but your Ubuntu partition now starts at sector 63. My guess - only a guess - is that the Windows repair console is trying to read sector 63 and can't, because it's a Linux filesystem. My guess - another guess - is that the answer would be to change the boot sector info, but I don't know how that would be done.

I'll contact another forum member who may have come across this problem before and ask them to have a look.

**EDIT**: or another answer *might* be to create a small NTFS primary partition starting at sector 63, but that would require you to shrink your Ubuntu partition.

---

### Post by oldfred on 2012-09-07
You can repair Windows boot sector with chkdsk and possibly fixBoot. Windows PBR (partition boot sector)  has the same partition info as the partition table and it must be correct. After Windows is resized it runs chkdsk which also updates the settings. Sometimes it may need fixBoot also and then another chkdsk.

You need both bootmgr & /bootBCD which were in Windows boot partition. I did see one user just copy bootmgr and BCD from his repairCD, but he had to edit BCD because it obviously was not for his install.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by rumpels110 on 2012-09-07
Hey guys,

thanks a lot for your replies. I already started command prompt using the install disk but without checkdisk. When I start diskpart, then

select disk 0
select partition 1
active

.... and then cancel diskpart, I am unable to run bootrec /fixboot, probably because of ext4?
Thus, I will select partition 2 (sda2) and rerun your commands again. Or must I do that on sda1?

I'm going to report. Thanks a lot!

---

### Post by coffeecat on 2012-09-07
> **rumpels110 said:**
> 
.... and then cancel diskpart, I am unable to run bootrec /fixboot, probably because of ext4?
Thus, I will select partition 2 (sda2) and rerun your commands again. Or must I do that on sda1?

I'm going to report. Thanks a lot!

Don't try and run any Windows commands on sda1. As far as Windows is concerned, a Linux partition is a mystery, and sda1 is now irrelevant to your situation with the Windows boot files. You must try to repair sda2.

---

### Post by rumpels110 on 2012-09-07
Now grub is not longer shown at startup. No chance to start Ubuntu or Win7 now. I am goong to run ubuntu install live cd and fix the mbr. goddamn, what complicated. 

I hear the heartbeat of both os, but I cant start them :/.

crazy stuff...

-----------
Update: Complete bootinfo after repair: [http://pastebin.com/WJL5nrTC](http://pastebin.com/WJL5nrTC)

---

### Post by oldfred on 2012-09-07
Script still looks the same.

When you said partition one & active that is the same as moving boot flag. 

You want sda2 to be the active or boot flagged partition. Then Windows repairs should see sda2 and repairs should work.

---

### Post by rumpels110 on 2012-09-07
Ok, thanks a lot for your patience.
I really tried my best and read a lot of articles resulting in the confession that this is very special in my case. When I do

bootrec /scanos,

... no OS is found. But Win and Ubuntu - both - realize that there is a installation. :/

"You need both - bootmgr & /bootBCD which were in Windows boot partition."
I really don't know where to copy them and how to configure grub then.

What do you think: Is there any realistic chance to let my Win7 os run again? I don't see a measure currently. Whatever I try, it doesn't bring the right results.
Would a fresh Win7 install work although there is a "unreadable" ext4 partition with the grub loader? I am totally confused, that I have to reinstall all that software due to a small amount of boot files I would need at the right place.

Maydaaaaay ://

---

### Post by oldfred on 2012-09-07
did chkdsk run to completion without any errors on sda2? That has to run first. Then perhaps fixBoot and another chkdsk. The partition boot sector PBR has to be a valid NTFS partition boot sector for Windows to even start repairs and find the install.

Are you using a full install or repairCD/USB?

Then bootmgr file should be in the root of your CD and /boot/BCD should also be there. You then should be able to copy. I do not know commands in Windows anymore, but a simple copy from one drive to another of the /boot folder and bootmgr file. But again until PBR is fixed Windows CD may not even see it correctly as a "drive".

---

### Post by rumpels110 on 2012-09-07
Hey Olfred,

chkdsk ran without error on both options. Should I copy the files from CD to sda2? Since they already exist. The operating system is shown in windows repair console now. Its magic. It is also shown in the grub dropdown:

When I chose it, the message "a disk read error occured". Since I flagged sda2 as boot via boot-repair, the error is not longer shown but only a black screen with a blinking cursor.

This ist my bootscript info: [http://paste.ubuntu.com/1191658/](http://paste.ubuntu.com/1191658/)

Thanks a lot for your help!

---

### Post by oldfred on 2012-09-07
This still is wrong?? I thought chkdsk and/or boot repair would fix it. Did you run chkdsk on sda2? It now has boot files so that is good. Not sure if then BCD is correct or not as we cannot see that.

> sda2: _____________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 41945778.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
Beyond that, perhaps some of the Windows third party repair tools might work. Windows does not always have the best tools.

I prefer grub2 over easyBCD, but sometimes it can repair things.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
Also third-party tool, such as Partition Wizard MiniTool or EASEUS 
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by rumpels110 on 2012-09-07
Some of that tools need windows installation. :/

I don't see a chance to cope with that problem. So sick, since this all happens because of some kb's...

If I reinstall Windows7 now, does someone know here if Ubuntu on sda1 can be found after the installation or do I need to fix via liveCD and cannot start Windows after that, which seems to be a endless cycle?

*Daaaaaaaaaaaaaaaaaaaaaaaaaamn shxxxXXx" ://

---

### Post by oldfred on 2012-09-07
Another thought.

Just run chkdsk. 

I ran chkdsk from a Windows 7 repairCD on my XP install and it wrote a new PBR. In testdisk I can compare them and I could see it calling out bootmgr. My backup called out ntldr which is what I needed for XP. So I know chkdsk writes a new PBR.

I wonder now if fixBoot only copies the backup back to the original and since the backup is also bad fixBoot makes it worse??

---

### Post by offgridguy on 2012-09-08
> **critin said:**
> Doesn't Windows have to be Primary?

I know linux can be logical or primary, but I didn't think windows could.

I just installed ubuntu alongside windows in my laptop, on reboot ubuntu is
always primary.  Windows must be selected, no problem, but it doesn't give
you much time to do it.

---

### Post by coffeecat on 2012-09-08
> **offgridguy said:**
> I just installed ubuntu alongside windows in my laptop, on reboot ubuntu is
always primary.  Windows must be selected, no problem, but it doesn't give
you much time to do it.

This is not what critin was referring to as "primary". You appear to be referring to the grub boot menu. critin was referring to a primary partition - Windows must be on a primary partition in order to be able to boot, or have its boot files on a primary partition. Linux does not have this limitation and can boot from a logical partition.

This is what this thread has been about, not the order of items in the grub menu.

---

### Post by offgridguy on 2012-09-08
Thank you for the clarification.

---

