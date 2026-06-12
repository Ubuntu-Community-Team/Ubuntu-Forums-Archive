---
title: "Have I lost the files in my hard drive??"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by heather8 on 2016-01-22
I followed the directions here: [http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/) to clone my hard drive.  This is what I got after cloning:

```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe28236a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *      206848  1953522687   976657920    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe28236a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *      206848  1953522687   976657920    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdc
dd: error reading ‘/dev/sda’: Input/output error
15268408+0 records in
15268408+0 records out
7817424896 bytes (7.8 GB) copied, 4500.23 s, 1.7 MB/s
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8002 MB, 8002732032 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15630336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15630335     7815152    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6df0355

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
ubuntu@ubuntu:~$

```

When I run sudo parted -l, I get this:

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  525MB   524MB   fat32        EFI system partition          boot
 2      525MB   567MB   41.9MB  fat32        Basic data partition          hidden
 3      567MB   701MB   134MB                Microsoft reserved partition  msftres
 4      701MB   1215MB  514MB   ntfs         Basic data partition          hidden, diag
 5      1215MB  491GB   490GB   ntfs         Basic data partition          msftdata
 6      491GB   492GB   496MB   ntfs                                       hidden, diag
 7      492GB   500GB   8121MB  ntfs         Microsoft recovery partition  hidden, diag


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 8003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8003MB  8003MB  primary  fat32        boot


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  525MB   524MB   fat32        EFI system partition          boot
 2      525MB   567MB   41.9MB  fat32        Basic data partition          hidden
 3      567MB   701MB   134MB                Microsoft reserved partition  msftres
 4      701MB   1215MB  514MB   ntfs         Basic data partition          hidden, diag
 5      1215MB  491GB   490GB   ntfs         Basic data partition          msftdata
 6      491GB   492GB   496MB                                              hidden, diag
 7      492GB   500GB   8121MB               Microsoft recovery partition  hidden, diag


ubuntu@ubuntu:~$

```

I tried using the cloned drive to access files and I was not able to.  I get this error:
```

Sorry, could not display all the contents of “D424D74A24D72DEC1”: Error when getting information for file '/media/ubuntu/D424D74A24D72DEC1/MSOCache': Input/output error

```

Can someone please help.  I'm not sure what I did wrong or what I am supposed to do from here.  I really need these files cloned before my hard drive is completely inaccessible.

---

### Post by oldos2er on 2016-01-22
You need to use *gdisk* for GPT partitions, not fdisk. And since GPT is a proprietary Microsoft thing, it'd be best to use Microsoft tools on those partitions rather than Linux ones--I don't know if even are any that would work.

---

### Post by heather8 on 2016-01-22
> **oldos2er said:**
> You need to use *gdisk* for GPT partitions, not fdisk. And since GPT is a proprietary Microsoft thing, it'd be best to use Microsoft tools on those partitions rather than Linux ones--I don't know if even are any that would work.

So are you saying there is no way to get my files from my dwindling hard drive onto another drive to put onto the new hard drive I will be putting in my laptop?  How would I even go about looking to find something to help?

I am no longer able to access the files on my hard drive.  I get this error when I try:

```

Error mounting /dev/sda5 at /media/ubuntu/D424D74A24D72DEC: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda5" "/media/ubuntu/D424D74A24D72DEC"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

What does this mean and what can I do?

---

### Post by deadflowr on 2016-01-22
> The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting)


You need to boot windows and do a full system shutdown.
Windows defaults to a funky hibernate-thingy shutdown.
I don't run windows, so can't elaborate, but you can read about how to do this from a windows-related forums, here:
[http://www.tenforums.com/tutorials/7418-shut-down-computer-windows-10-a.html](http://www.tenforums.com/tutorials/7418-shut-down-computer-windows-10-a.html)


Edit: Also you can use parted to read gpt-set drives.
instead of fdisk -l, use parted -l
```
sudo parted -l
```

---

### Post by Petro Dawg on 2016-01-23
> **deadflowr said:**
> You need to boot windows and do a full system shutdown.
Windows defaults to a funky hibernate-thingy shutdown.
I don't run windows, so can't elaborate, but you can read about how to do this from a windows-related forums, here:


Just to expand on this a bit.  Win10 by default goes into hibernate when you select the shutdown option to make starting up faster (fast boot).  This setting can be turned off somewhere in the control panel settings, or you can just simply select "restart" instead of "shut down" and then manually turn off the computer (press the power button) after it has shut down but before windows has a chance to reboot.

---

### Post by leunam12 on 2016-01-23
Let's guide you in this task. First of all what do you mean when you say "clone" what do you mean? Do you want to make an exact replica of your hard drive or do you want to just recover your files and documents? Either way the first thing that you have to do is post the results of ```
lsblk
```, then, after we identify the source and destination drives I'll tell you how to mount a hibernated drive.

---

### Post by oldfred on 2016-01-23
Also duplicate UUIDs are not allowed. So once you clone drive, you cannot have both mounted at the same time. And if you try to, it may mount one or the other and get systems really out of sync. Part of one drive may be updated and part of the other.

And with gpt(GUID) the GUID's are also in the partition table & backup partition table. So you can only clone an entire drive or you get GUID out of sync. May be possible to repair, but better to copy data not clone if copying a partition with gpt.

---

### Post by oldos2er on 2016-01-23
> **heather8 said:**
> So are you saying there is no way to get my files from my dwindling hard drive onto another drive to put onto the new hard drive I will be putting in my laptop?  How would I even go about looking to find something to help?

Look for a good Windows support forum? I don't use Windows, so maybe someone who does can point you to one.

---

### Post by heather8 on 2016-01-26
> **leunam12 said:**
> Let's guide you in this task. First of all what do you mean when you say "clone" what do you mean? Do you want to make an exact replica of your hard drive or do you want to just recover your files and documents? Either way the first thing that you have to do is post the results of ```
lsblk
```, then, after we identify the source and destination drives I'll tell you how to mount a hibernated drive.

I just want to recover my files and documents and put them on the new hard drive I will be putting in.

```

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   500M  0 part 
&#9500;&#9472;sda2   8:2    0    40M  0 part 
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9500;&#9472;sda4   8:4    0   490M  0 part 
&#9500;&#9472;sda5   8:5    0 456.6G  0 part 
&#9500;&#9472;sda6   8:6    0   473M  0 part 
&#9492;&#9472;sda7   8:7    0   7.6G  0 part 
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0 962.1M  1 loop /rofs


```

---

### Post by oldfred on 2016-01-26
Lets see all the details at once:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Your list above did not show 1TB drive? Was it plugged in?
Can you directly boot Windows from UEFI boot tab or one time boot key like f10 or f12? Then make sure Windows fast start up is off as posted above.

---

### Post by leunam12 on 2016-01-26
Ok, it seems that you have a 500GB hard drive installed on your computer and that you are booting from an 8GB USB stick. You still have to plug in your removable drive where you are going to be transferring your files to, right now it does not appear as an available drive. The partition where you have your files that you want to recover is sda5. Open the terminal and type ```
sudo mkdir /media/WinHDD
```and press ENTER. 
Hopefully is not going to give you an error and a new directory named "WinHDD" will be created in /media.
Now open the file manager, drag the window so that the terminal and the file manager are side by side, and go back to the terminal.
Now type```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /media/WinHDD
```A little symbol will appear on the left pane of the file manager, next to the drive that you just mounted. Click on it (the drive not the little symbol) and see if you can access your files. If you can access your files then you are ready to start copying. Your files are most likely in your profile folder, it would be something like this:```
/media/WinHDD/Users/<whatever_user_name_you_had_in_Windows>/
```Let me know if you can see your files or if you need further assistance.

Probably the best way to copy your files is with rsync. type lsblk on the terminal and press enter, then connect your removable hard drive, wait until it mounts  and do lsblk again you will see the new drive (probably /dev/sdc1) and the mount point. Create a new directory like this ```
mkdir /whatever/mountpoint/Backup
```. Example: if the mount point next to the removable drive is /media/StorageDrive you will do ```
mkdir /media/StorageDrive/Backup/
```
Now, to copy your files this is the command ```
rsync -avP /media/WinHDD/Users/your_user_name_in_Windows/ /media/StorageDrive/Backup
```
Let me know if you have any doubts or questions.

---

### Post by heather8 on 2016-01-27
> **oldfred said:**
> Lets see all the details at once:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Your list above did not show 1TB drive? Was it plugged in?
Can you directly boot Windows from UEFI boot tab or one time boot key like f10 or f12? Then make sure Windows fast start up is off as posted above.

[http://paste.ubuntu.com/14681065/](http://paste.ubuntu.com/14681065/)
No, I didn't have the 1TB drive plugged in.  I do now.  I cannot get to Windows at all.  All I get is the Dell splash screen and then either a repairing message, or a spinning circle.

> **leunam12 said:**
> 
Now open the file manager, drag the window so that the terminal and the file manager are side by side, and go back to the terminal.
Now type```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /media/WinHDD
```A little symbol will appear on the left pane of the file manager, next to the drive that you just mounted. Click on it (the drive not the little symbol) and see if you can access your files. If you can access your files then you are ready to start copying. Your files are most likely in your profile folder, it would be something like this:```
/media/WinHDD/Users/<whatever_user_name_you_had_in_Windows>/
```Let me know if you can see your files or if you need further assistance.

This is what I got after:

```

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /media/WinHDD
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
ubuntu@ubuntu:~$ 


```

There was not a symbol

---

### Post by oldfred on 2016-01-27
You cannot then have external drive plugged in and have system work. It is just a clone that you put on shelf until internal drive fails. 

You have duplicate UUIDs and system will not work with duplicates. You show no Linux partitions.
Highlighted first of duplicates:
```
/dev/sda1        [COLOR=#ff0000]7C54-1F3F[/COLOR]                              vfat       ESP
/dev/sda2        0648-CE5F                              vfat       DIAGS
/dev/sda4        226E4AFE6E4AC9ED                       ntfs       WINRETOOLS
/dev/sda5        D424D74A24D72DEC                       ntfs       
/dev/sda6        4032F0FF32F0FB2C                       ntfs       
/dev/sda7        EC6453FD6453C94A                       ntfs       PBR Image
/dev/sdb1        8563-D229                              vfat       UUI
/dev/sdc1        [COLOR=#ff0000]7C54-1F3F[/COLOR]                              vfat       ESP
/dev/sdc2        0648-CE5F                              vfat       DIAGS
/dev/sdc4        226E4AFE6E4AC9ED                       ntfs       WINRETOOLS
/dev/sdc5        D424D74A24D72DEC                       ntfs       

```

It also looks like you left Windows fast start up on, which is always on hibernation. You need to directly boot Windows from UEFI boot menu or perhaps one time boot like like f10 or f12, check your manual for correct keys. External must be then unplugged.

 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by heather8 on 2016-01-27
> **oldfred said:**
> You cannot then have external drive plugged in and have system work. It is just a clone that you put on shelf until internal drive fails. 

You have duplicate UUIDs and system will not work with duplicates. You show no Linux partitions.
Highlighted first of duplicates:
```
/dev/sda1        [COLOR=#ff0000]7C54-1F3F[/COLOR]                              vfat       ESP
/dev/sda2        0648-CE5F                              vfat       DIAGS
/dev/sda4        226E4AFE6E4AC9ED                       ntfs       WINRETOOLS
/dev/sda5        D424D74A24D72DEC                       ntfs       
/dev/sda6        4032F0FF32F0FB2C                       ntfs       
/dev/sda7        EC6453FD6453C94A                       ntfs       PBR Image
/dev/sdb1        8563-D229                              vfat       UUI
/dev/sdc1        [COLOR=#ff0000]7C54-1F3F[/COLOR]                              vfat       ESP
/dev/sdc2        0648-CE5F                              vfat       DIAGS
/dev/sdc4        226E4AFE6E4AC9ED                       ntfs       WINRETOOLS
/dev/sdc5        D424D74A24D72DEC                       ntfs       

```

It also looks like you left Windows fast start up on, which is always on hibernation. You need to directly boot Windows from UEFI boot menu or perhaps one time boot like like f10 or f12, check your manual for correct keys. External must be then unplugged.

 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)


I can't get Windows to do anything, just get the dell splash screen and either the "repairing" or the constantly moving circle.  Even with my external hard drive (that I tried to put my cloned drive on) unplugged, I still can't access anything in the hard drive (while running from the ubuntu memory stick because windows is not working).  The only way I can get anything to come on my laptop besides that splash screen is to use the memory stick that has ubuntu on it.

---

### Post by oldfred on 2016-01-27
You are then into Windows repair and this is an Ubuntu forum. A few dual boot and know some Windows fixes, but you may do better in a Windows forum. Boot-Repair and Linux can only make minor fixes to Windows.

Have you tried f8 as soon as you try to start Windows to see if you can get into its internal repair console. Otherwise you need your Windows repair flash drive to make repairs.
And if it is running chkdsk it may take a while.

Windows forums:
 [http://www.tenforums.com/](http://www.tenforums.com/)
[http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

You do have a way to repair Windows?

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by leunam12 on 2016-01-28
```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /media/WinHDD
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```
Why don't you try the read-only option as suggested in the last line?
```
sudo mount -t ntfs-3g -o ro /dev/sda5 /media/WinHDD
```

---

