---
title: "HP laptop comes with all 4 primary partitions used"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by jflinux on 2013-05-31
HP laptop comes with all 4 primary partitions used.
No available partitions to install ubuntu.
So I shrank the c: drive and now have 200GB of unused space.
I have to delete a primary partition and create an extended partition and put logical partitions in it.

This sort of solve my problem:
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/m-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/m-p/742019)

So I want to delete the HP_TOOLS partiton and put HP_TOOLS on a usb stick.
1. How?
or 
save HP_TOOLS directory or backup DVD and reinstall it as a logical partition inside the to be created extended partition.
2. How?

bonus question.
Is 1 partiton with / and 1 partition for swap best practice now?

Thanks in advance
-J

---

### Post by Mark Phelps on 2013-06-01
First off, boot into Windows and use Windows Explorer to copy the entire contents of the HP_TOOLS partition to a directory on your drive.  That will give you access to the tools after you remove the partition.

Then, using the Windows Disk Management tool, remove the HP_TOOLS partition.

Then, using the same tool, shrink down your Windows OS partition.  It may have to reboot to do this -- so be prepared.

After that, boot into Windows a couple of times to allow its filesystem to make any needed adjustments.

Then, boot from the Ubuntu DVD/USB and use "something else" to create the partitions.

---

### Post by fantab on 2013-06-01
If you have GUID partition table then you don't need to delete any partition. With GPT you can have more than 100 primary partitions.

Do you have Windows8 preinstalled and booting with UEFI? If you do then the chances are you are using GPT.

---

### Post by Impavidus on 2013-06-01
This post by SeijiSensei may be useful to you: [http://ubuntuforums.org/showthread.php?p=11299287#post11299287](http://ubuntuforums.org/showthread.php?p=11299287#post11299287)

---

### Post by jflinux on 2013-06-02
Thanks to all the replies.  How can I tell if I have UEFI?  
I have windows7 and can get into something that looks like BIOS screens at boot time by pressing some keyboard keys.
But what does UEFI look like and is it different than regular BIOS?

---

### Post by fantab on 2013-06-03
Boot with Ubutnu LiveDVD/USB and 'Try Ubuntu Without Installing". When desktop is loaded open 'Terminal' [ctrl+alt+t] and run following commands:

```
sudo fdisk -l
```

Post the output here.

```
sudo parted -l
```

Post the output here.

---

### Post by jflinux on 2013-06-03
By the way, thanks for the info about GUID partitions.  Thought we were still stuck with Master Boot Record.
---
[FONT=arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]
[FONT=arial]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 60801 cylinders[/FONT]
[FONT=arial]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x477abf56[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1   *           1          26      203776    7  HPFS/NTFS[/FONT]
[FONT=arial]Partition 1 does not end on cylinder boundary.[/FONT]
[FONT=arial]/dev/sda2              26       30975   248598528    7  HPFS/NTFS[/FONT]
[FONT=arial]/dev/sda3           58276       60284    16130048    7  HPFS/NTFS[/FONT]
[FONT=arial]/dev/sda4           60284       60802     4160536    c  W95 FAT32 (LBA)[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT]
[FONT=arial]Model: ATA ST9500325AS (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 500GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]

[FONT=arial]Number  Start   End    Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      1049kB  210MB  209MB   primary  ntfs         boot[/FONT]
[FONT=arial] 2      210MB   255GB  255GB   primary  ntfs[/FONT]
[FONT=arial] 3      479GB   496GB  16.5GB  primary  ntfs[/FONT]
[FONT=arial] 4      496GB   500GB  4260MB  primary  fat32        lba[/FONT]

[FONT=arial]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT]
[FONT=arial]has been opened read-only.[/FONT]
[FONT=arial]Error: /dev/sr0: unrecognised disk label[/FONT]
[FONT=arial]ubuntu@ubuntu:~$[/FONT]

---

### Post by fantab on 2013-06-03
> **jflinux said:**
> By the way, thanks for the info about GUID partitions.  Thought we were still stuck with Master Boot Record.
---
[FONT=arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT]

[FONT=arial]Model: ATA ST9500325AS (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 500GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
_**[FONT=arial]Partition Table: msdos[/FONT]**_

[FONT=arial]Number  Start   End    Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      1049kB  210MB  209MB   primary  ntfs         boot[/FONT]
[FONT=arial] 2      210MB   255GB  255GB   primary  ntfs[/FONT]
[FONT=arial] 3      479GB   496GB  16.5GB  primary  ntfs[/FONT]
[FONT=arial] 4      496GB   500GB  4260MB  primary  fat32        lba[/FONT]

[FONT=arial]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT]
[FONT=arial]has been opened read-only.[/FONT]
[FONT=arial]Error: /dev/sr0: unrecognised disk label[/FONT]
[FONT=arial]ubuntu@ubuntu:~$[/FONT]

You have 'msdos' table. and you are not booting with UEFI. In other words, you are stuck with FOUR PRIMARY Partitions LIMIT, and you have to delete one partition to create an EXTENDED Partition, which in turn can contain more than 100 LOGICAL Paritions.

But before you delete any partitions, I suggest you do COMPLETE backup of your Hard Disk with partitions and data. To do this: 
Shrink Windows Partition using 'Windows Disk Management' making 'unallocated space' enough to install Ubuntu. Do not partition this space, leave it 'unallocated'. Do a BACKUP following instrucitions and tool to do so, suggest below.
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710) , here is the tool [Macrium Reflect ]("http://www.macrium.com/reflectfree.aspx")

Now copy all the contents of the HP Utilities partitions on somewhere in Windows and Delete that parition using Windows Disk Management. Reboot Windows a couple to times.
Install Ubuntu.

---

### Post by mastablasta on 2013-06-03
there is a tool that converts prrmary partition into secondary. thoguh you would sitll need to backup your data. and depending what is on your hp_tools (cause on mine is bootable live linux OS with persistance) you could chose either windows system partition to be secondary or hp_tools.

to backup data or image partition to external drive i suggest Redobackup (it's really easy to use) or Clonezilla (a bit more difficult to use but with more options).

---

### Post by Mark Phelps on 2013-06-03
I already told you what you need to do -- in detail -- way back in post #2. IF you start messing around with changing the System partition from Primary to Secondary, you risk corrupting the boot and rendering Windows unbootable.

---

### Post by mastablasta on 2013-06-03
> **Mark Phelps said:**
> I already told you what you need to do -- in detail -- way back in post #2. IF you start messing around with changing the System partition from Primary to Secondary, you risk corrupting the boot and rendering Windows unbootable.


even if hp_tools has an operating system on it that is started by a different key than the "on key"?

---

### Post by Mark Phelps on 2013-06-03
> **mastablasta said:**
> even if hp_tools has an operating system on it that is started by a different key than the "on key"?

The only other "operating system" I've encountered with HP_TOOLS is WinPE -- and I don't use that anyway.  The advice was to retain the software in that partition so it could be removed.  The other advice I've typically seen in this forum is simply to REMOVE that partition, as folks call it "bloatware".

---

### Post by jflinux on 2013-06-03
Thanks Mark.  
 I had thought it was bloatware. 
Too bad they are not forward thinking at HP to realize using all the partitions is like
soldering DRAM to the motherboard: it blocks adaptability and upgrades.  
I now regret having bought an HP and will tell my friends to avoid HP until they fix this problem they
created.  
The reason I didn't go ahead and just delete hp tools is if you call hp support they want you to run their tools in order
to get warranty, maybe?  Plus I got busy with other things,  so I haven't had a chance to try you solution.

I was also worried that a bootable partition (like HP_TOOLS) might need special formatting
or special data in sector 1 of the HP_TOOLS in order to be bootable. 
I remember in the old days a bootable floppy had hidden files and other special
formatting?
I just don't know much about bootloaders and boot sequence things.
So, I  will read a little more about bootloaders and try your solution this weekend.
I'll report back on progress.

---

