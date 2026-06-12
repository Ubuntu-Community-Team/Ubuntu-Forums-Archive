---
title: "Partitioning with sfdisk"
date: 2018-10-20
forum: New to Ubuntu
---

### Post by 1awc on 2018-10-20
I've messed up my dual 750GB dual boot (Windows 8.1-preinstalled & Ubuntu 14.04) HDD. I am trying to restore my partition table without formatting as I want to try and recover some files with a Windows search.  I only have a partial Deja-dup backup and this photo of the fdisk and lsblk output of the partition table taken shortly after I started having problems. I'm using a Ubuntu Live USB on the 4GB (3.5GB) drive.  The 114GB drive is a USB I'm using for downloading & storage to limit writing on the HDD. 
[ATTACH=CONFIG]281390[/ATTACH]

I tried Testdisk and saved some files but when restoring the partition table I get a mess of 20 1.5-22MB partitions and one 600+MB. Gparted is graphical and, as far as I know, will not allow me to numerically set the partition start and end--hence sfdisk,

If I write a file identical to an sfdisk (old version) dump ```
sfdisk -d /dev/sda
``` named "**created_dump.txt**" using the info from my fdisk photo,  I can use ```
sfdisk --force /dev/sdX < created_dump.txt
``` to make a new partition table identical to the fdisk output photo without formatting. 

As you will see, sfdisk does not have "end" and  "sectors" columns so using the columns from fdisk and the formula below I have calculated the sizes. When I do, my total is -1 from the fdisk results in the photo so I have added the "+".

End-Start=Sectors
Sectors*bytes (512)=bytes
bytes/1024=kilobytes
kilobytes/1024= megabytes
megabytes/1024=gigabytes

**created_dump.txt**
```
# partition table of /dev/sda
unit: sectors
  
/dev/sda1 :      start=     2048,         size=    4194304+,         Id=   7      Recovery
/dev/sda2 :      start=     821248,       size=    3145728+,         Id=   7      ESP
/dev/sda3 :      start=     1697792,      size=    469203156992+,    Id=   7      Gateway
/dev/sda4 :      start=     918110208,    size=    253961913586+,    Id=  83
/dev/sda5 :      start=     1450706944,   size=    3443351269+,      Id=  82
/dev/sda6 :      start=     1457928184,   size=    15+,              Id=  82

```

My questions:
Does everything in the **created_dump.txt** look correct? fdisk says that sda4 is Microsoft basic data which would be NTFS  Id=82 but lsblk says sda4 is ext4 which would be Id=83.  Which one is it and how would I know? 

I would appreciate any help.  I need step-by-step detailed instructions. If there is a better way to accomplish what I'm trying to do please let me know, I am open to whatever works.

---

### Post by oldfred on 2018-10-20
Fdisk & sfdisk recently got major updates to support gpt partitioned drives.

You need to be using the newer version. My 18.04 has it and file looks like this:
```
label: gpt
label-id: 1AB0DBE4-1876-4F34-81EA-F2C2B2B55B74
device: /dev/sdb
unit: sectors
first-lba: 34
last-lba: 1953525134

/dev/sdb1 : start=        2048, size=     1044480, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=E58602B1-8FC4-46D1-991F-1D6511D9CDF4, name="EFI System Partition"
```


You may be able to use gdisk, but I think it is a binary file.
       sudo sgdisk --backup=table /dev/sda

---

### Post by 1awc on 2018-10-21
Hmm, okay.  Upgrading to 16.03 then downgrading back to 14.04 is what started my problems.  I used a Live CD 18.04 and took a look at sfdisk.  For rebuilding my partition table via text, how is sfdisk after v.2.26 any better?  The GUID string for GPT in the new version, but if I use the old version why would the GUID strings be of any benefit?

---

### Post by oldfred on 2018-10-21
I have been using gpt on all Ubuntu only drives since about 10.04 install to repartitioned gpt drive.
If using on a MBR(msdos) partitioned drive, I would assume it should be ok.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by 1awc on 2018-10-22
I cannot understand why you are highlighting the fact that it is a  GPT.  The disk has never been a MBR.  The info from fdisk (see photo in  original post) says "Disklabel type: gpt".  I'm trying to redo the  partition table on the *same* disk the *same* way it was  when the photo of the fdisk info was taken.  I did not know to do a  sfdisk dump three weeks ago and now it is pointless because everything  is messed up.  So, I wrote/created a new text file (created_dump.txt)to look like an a sfdisk dump (**-d**) and I'm trying to confirm that I created it correctly before I **-force** it to remake the partition table.

Does **sfdisk -force** with a text file only work on MBR and not GPT?  If so does anything like that exist for GPT?

---

### Post by oldfred on 2018-10-22
If using the older sfdisk, why 
I believe both the new sfdisk & gdisk work with gpt drives. Just do not use old sfdisk or fdisk as you found out.
I was pointing out that you only should use the older fdisk & sfdisk with the old MBR partitioning.

What ever you do you should have all data backed up, so if something does not work, it is not the end of the world.
Whenever you hand edit a file like that you have to be very careful to make sure spacing & structure match correctly. 
Best to have sfdisk create file and only do minor edits.

If trying to recover existing partitions, often better to use testdisk or parted rescue (again from newer Ubuntu live). 
The use of sfdisk is considered a last resort when other tools have totally failed.

       Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[URL="http://ubuntuforums.org/showthread.php?t=2315405"]http://ubuntuforums.org/showthread.php?t=2315405
      [/URL]
 [http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition) 
            Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    [URL="http://ubuntuforums.org/showthread.php?t=2315405"]
[/URL]

---

### Post by 1awc on 2018-10-28
Okay, now I understand about using old sfdisk.  

I've gotten some sleep and not so panicky.  Remembering, some of the data is still on the disk, it is just not accessible by the old references. 

I ran Testdisk, again, v7.0 on 18.04 after update. I got a lot of warnings that I am supposed to ignore but ended up with the same 20 +/- partitions.  I read the GNU Parted (rescue) and I am hopeful and will try it next instead of sfdisk.  
Will post results.

---

### Post by oldfred on 2018-10-28
If you have edit partitions multiple times, testdisk finds all the old versions, most will overlap and cannot be selected.
Best if you know or have good idea of which partitions you last have and at least approximate sizes.

---

### Post by 1awc on 2018-10-28
Yes, I have them from the [fdisk photo]("https://ubuntuforums.org/attachment.php?attachmentid=281390&d=1540060441").

---

### Post by 1awc on 2018-11-03
```

(parted) print                                                            
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start        End          Size        File system  Name  Flags
 2      2048s        821247s      819200s
 3      821248s      1435647s     614400s     ntfs
 4      1697792s     918110207s   916412416s  ntfs
 5      918110208s   1450706943s  532596736s  ext4
 6      1450706944s  1457928175s  7221232s    ext2
 1      1457928184s  1465147391s  7219208s

```

This is so annoying.  Above is the closest I ever got to what I had, but I no longer have that now.  NOTE: Number 1 End: 1465147391 not 1465147399 when I try  ```
 (parted) mkpart 
```  I get "is outside of the device".  I have 20+ partitions thanks to Testdisk.  Since, I have learned I cannot merge partitions so I used Testdisk again and restored one partition with the correct start and end.  Then expanded it with Gparted where I get "Failed to load module "canberra-gtk-module"" and then "invalid argument during seek for read on /dev/sda".  I still could not get No. 1 to End on the correct sector.  Is there any way I can force the partition original starts and ends without formatting?

---

### Post by oldfred on 2018-11-03
Do not understand why you cannot use the new sfdisk with correct data to restore partitions.
But you are missing the system reserved partition that is between the ESP & first NTFS. Most tools seem to miss it since it is unformatted. The only identifier is the GUID.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

And if you are missing the MSR/system reserved the start of you main NTFS will  be wrong. NTFS partition have in the first sector or PBR/Boot Sector information on the start and size of the NTFS partition which must match the partition table. Usually after resize you have to run chkdsk to update that info.
I have seen a lot of Windows dual boot systems with the system reserved. I think I filed a bug with Boot-Repair to stop saying it is unformatted/error as it has a valid GUID and is required by Microsoft. But I do not think it is really Boot-Repair, but which ever partition tools generates that part of report.

Look thru forum for Boot-Repair outputs with Windows systems showing the system reserved. Pastebin posts expire so you will need more recent posts, but there should be many.

---

### Post by 1awc on 2018-11-16
> **oldfred said:**
> Do not understand why you cannot use the new sfdisk with correct data to restore partitions.

I read somewhere that sfdisk was powerful and should only be used in extreme cases. I'm only as good as the last thing I read. ;)  I wasn't sure if my case was extreme and I'm afraid I will do something wrong and delete the remaining data.  Also, I can't seem to get it installed.  I have to find out the package where sfdisk is located. 

"[B]Package sfdisk is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or
is only available from another source[/B]"  
 
I found this Boot-Repair output [http://paste.ubuntu.com/p/rsGWKWxgVB/](http://paste.ubuntu.com/p/rsGWKWxgVB/) lines 613-630 below for future reference. /dev/nvme0n1p being the Microsoft Reserved Partition (MSR)--128 MB.

```
Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F52F55BD-D86F-443D-B197-124D7B418188

Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    534527    532480   260M EFI System
/dev/nvme0n1p2    534528    796671    262144   128M Microsoft reserved
/dev/nvme0n1p3    796672 215191551 214394880 102.2G Microsoft basic data
/dev/nvme0n1p4 496103424 500117503   4014080   1.9G Windows recovery environment
/dev/nvme0n1p5 291303424 322553855  31250432  14.9G Linux swap
/dev/nvme0n1p6 322553856 361615359  39061504  18.6G Linux filesystem
/dev/nvme0n1p7 361615360 496103423 134488064  64.1G Linux filesystem
/dev/nvme0n1p8 215191552 291303423  76111872  36.3G Microsoft basic data

Partition table entries are not in disk order.
```
 
Mine starts with a /dev/sda1 Recovery partition whereas this has a recovery on /dev/nvme0n1p4.

---

### Post by oldfred on 2018-11-16
Different vendors put recovery partitions and then ESP in different locations. And Microsoft reserved of 128MB is always just before first NTFS partition.
Since System reserved is unallocated space, most partition tools will not find it, and then try to recover Windows partition 128M as part of main NTFS which then causes issues.

Yours is definitely a major issue. But I would also make a sfdisk backup of whatever testdisk or parted rescue find. Then using a copy adjust to what is more correct for your system, if you know. If not it becomes a guess.

And you are correct, sfdisk should be reserved for extreme cases. I only have seen a few where testdisk or parted rescue did not work. And then very few that tried to use sfdisk.

---

### Post by 1awc on 2018-12-14
I'm stumped.

  I created "[created_dump.tx]("https://ubuntuforums.org//ubuntuforums.org/showthread.php?t=2404145&p=13810146#post13810146")t"  and then removed the spaces, +, and the partition types (not the IDs) because I was getting the error "```
>>> line 2: unsupported command
```". 
Now I am getting
```
>>> Created a new GPT disklabel (GUID: 719710E0-2EC7-BE47-8168-C3537B6A89D4).
/dev/sda1: Created a new partition 1 of type 'PowerPC PReP boot' and of size 2 GiB.
/dev/sda2: Sector 821248 already used.
Failed to add #2 partition: Numerical result out of range
```

According to my [fdisk photo]("https://ubuntuforums.org/attachment.php?attachmentid=281390&d=1540060441") , Sector 821248 should be available.  How do I force it to start partition 2 on Sector 821248 or can I remove all of the existing partitions and make new partitions on the disk without deleting data?

**Current partitioning:**
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 998D880B-E34D-124E-AF21-A1A4DD2FE0AC

Device          Start        End   Sectors  Size Type
/dev/sda1   918110208 1450706943 532596736  254G Microsoft basic data
/dev/sda2  1457928184 1457928199        16    8K Linux swap
```

BTW, FYI, sfdisk 2.26-3.0 -uM option does not work
Better for converting sectors to MB [https://geek-gogie.blogspot.com/2013/08/converting-sectors-into-mb.html](https://geek-gogie.blogspot.com/2013/08/converting-sectors-into-mb.html)

---

### Post by oldfred on 2018-12-14
Does not your screenshot show start & size in sectors.
[https://ubuntuforums.org/attachment.php?attachmentid=281390&d=1540060441](https://ubuntuforums.org/attachment.php?attachmentid=281390&d=1540060441)
With terminal output better to just copy & paste, and then if longer use code tags which also preserves formatting.

My 18.04 has this:
Welcome to sfdisk (util-linux 2.31.1).

This is the details I get. 
The man page on sfdisk has all the details on struction of file.
man sfdisk

```
fred@Bionic-Z170N:~$ sudo fdisk -l /dev/sdb
[sudo] password for fred: 
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1AB0DBE4-1876-4F34-81EA-F2C2B2B55B74

Device          Start        End   Sectors   Size Type
/dev/sdb1        2048    1046968   1044921 510.2M EFI System
/dev/sdb2   102606848  166094847  63488000  30.3G Linux filesystem
/dev/sdb3  1844776960 1949222911 104445952  49.8G Linux filesystem
/dev/sdb4  1535315968 1844776959 309460992 147.6G Linux filesystem
/dev/sdb5   166094848  229582847  63488000  30.3G Linux filesystem
/dev/sdb6   229582848  864462847 634880000 302.8G Linux filesystem
/dev/sdb7  1949222912 1953523711   4300800   2.1G Linux swap
/dev/sdb8     1048576   52248575  51200000  24.4G Linux filesystem
```

```
label: gpt
label-id: 1AB0DBE4-1876-4F34-81EA-F2C2B2B55B74
device: /dev/sdb
unit: sectors
first-lba: 34
last-lba: 1953525134

/dev/sdb1 : start=        2048, size=     1044921, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=E58602B1-8FC4-46D1-991F-1D6511D9CDF4, name="EFI System Partition"
/dev/sdb2 : start=   102606848, size=    63488000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=D4037A82-798B-4DDA-A5A7-BD16D5C0E81E, name="bionic_b"
/dev/sdb3 : start=  1844776960, size=   104445952, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=220B88E5-F8AF-4C10-8053-EFE2E843BF9C, name="ISO_b"
/dev/sdb4 : start=  1535315968, size=   309460992, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=AFC7DD01-0720-4272-97E7-B9E359D565C6, name="backup_b"
/dev/sdb5 : start=   166094848, size=    63488000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=EA548F34-9B12-4196-8AA6-E7EB9C0797DF, name="cosmic"
/dev/sdb6 : start=   229582848, size=   634880000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=D8D6A9E0-9FFA-4D7A-874D-E7ECCCF3195C, name="data"
/dev/sdb7 : start=  1949222912, size=     4300800, type=0657FD6D-A4AB-43C4-84E5-0933C84B4F4F, uuid=D7090376-3479-46EF-A3EE-DBA7C351D607
/dev/sdb8 : start=     1048576, size=    51200000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=85F3987A-8DE4-489A-8113-8DF837648938, name="disco"
```

---

### Post by 1awc on 2018-12-15
Yes, it shows sizes in sectors. 

 I thought about using MB instead of sectors when you said I needed to add the Microsoft Reserved Partition (MSR)/system reserved--128 MB.  Since it didn't show up in my screenshot, I wanted to make sure it was the right size and I'm more confident with sizes in MB/GB than in sectors.  

I thought the -f option was supposed to "force" the partitioning.  Yet, I keep getting the "Sector 821248 already used" error. It is in the unallocated space.

---

### Post by 1awc on 2018-12-17
I was unsuccessful with sfdisk so I switched to [(parted)]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=2ahUKEwj8g6Sxh6jfAhWntVkKHbFmCxgQFjABegQICRAB&url=http%3A%2F%2Fmanpages.ubuntu.com%2Fmanpages%2Ftrusty%2Fman8%2Fparted.8.html&usg=AOvVaw1cVWKY5eKMjsGjMeIxNVlZ"). It took more time since it is not scripted and when I made an error I used [Testdisk]("https://www.cgsecurity.org/wiki/TestDisk") which always found partition #1 and restored it.  Thereby "erasing" my error.  I'm not confident about the file systems so my next step is to clean it up, if need be.

---

### Post by oldfred on 2018-12-17
Is your partition 5 really ext2 or is the the unformatted Microsoft reserved?

I would backup current partition table you have as that then is a good starting point for further edits if you need it.

---

### Post by 1awc on 2018-12-18
> **oldfred said:**
> Is your partition 5 really ext2 or is the the unformatted Microsoft reserved?


Yes, it is the unformatted Microsoft reserved.  (parted) selected ext2 because I didn't enter anything.  I plan to find "something" to change it.  I am thinking Gparted but I need to read more.
Thanks for the backup reminder.

---

### Post by oldfred on 2018-12-18
Gparted or Windows partitioning tools will change partition.
With gparted you have to change to unformatted or cleared and then set msftres flag (not msftdata).

[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

---

### Post by 1awc on 2018-12-31
As you suggested, I used Gparted, changed the partition to unformatted then set the flag to msftres.
However the fdisk print```
Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B0E30354-A0B7-6649-83EA-65CAFF16777F

Device          Start        End   Sectors  Size Type
/dev/sdc1  1457928184 1457928199        16    8K Linux swap
/dev/sdc2        2048     821247    819200  400M Microsoft basic data
/dev/sdc3      821248    1435647    614400  300M Microsoft basic data
/dev/sdc4     1697792  918110207 916412416  437G Microsoft basic data
/dev/sdc5     1435648    1691647    256000  125M Microsoft reserved
/dev/sdc6   918110208 1450706943 532596736  254G Linux filesystem
/dev/sdc7  1450706944 1457928175   7221232  3.5G Linux filesystem

Partition table entries are not in disk order.
``` shows a "Microsoft reserved" you said that "most partition tools will not find it" is it showing up now because it has a flag or have I done something wrong?  My next step is to reinstall Windows (as it was the pre-installed OS) and I got the error "the disk where Windows is installed is locked".  Is it related?
[U]
**Changing Disk Identifier**[/U]

I needed to change the  filesystem UUID a.k.a. Disk Identifier--Please note it is for the disk not the partitions on the disk. I used fdisk as explained in this [post]("https://www.linuxquestions.org/questions/linux-general-1/what-is-disk-identifier-740408/#post4088044").  The Disk Identifier is not very important for Ubuntu but it is for Windows and I had/restoring a dual boot.

After using the "i" command, do not copy/paste all of replacement Disk Identifier characters.  It will not be  accepted. Copy/paste all characters except the last character then type that in and the  entire Identifier will be accepted.  

After entering the replacement Disk Identifier, the "w" command must be added at "Command (m for help):" prompt.  It will not work in expert mode.

```
Expert command (m for help): w
w: unknown command
```
In standard mode
```
Command (m for help): w
The partition table has been altered.
Syncing disks.
```

Enter command "p" to check your changes.  Then reboot, reinstall fdisk and check again to confirm.

---

### Post by oldfred on 2018-12-31
Do parted or gdisk show more info.
I stopped using fdisk myself years ago as it did not support gpt. New version now does.
sudo parted -l
sudo gdisk /dev/sdc -l

---

### Post by 1awc on 2018-12-31
My results : 
```
$ sudo parted -l

Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sdd: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name      Flags
 2      1049kB  420MB  419MB                   Recovery  msftdata
 3      420MB   735MB  315MB                   ESP       msftdata
 5      735MB   866MB  131MB                             msftres
 4      869MB   470GB  469GB                   Gateway   msftdata
 6      470GB   743GB  273GB   ntfs
 7      743GB   746GB  3697MB  linux-swap(v1)
 1      746GB   746GB  8192B

```
and from
```
$ sudo gdisk /dev/sdd -l 
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 1465149168 sectors, 698.6 GiB
Model: TOSHIBA MQ01ABD0
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 032E6588-4EBB-EA4B-9311-4FAA44B413C9
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 8-sector boundaries
Total free space is 7229101 sectors (3.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1      1457928184      1457928199   8.0 KiB     8200  
   2            2048          821247   400.0 MiB   0700  Recovery
   3          821248         1435647   300.0 MiB   0700  ESP
   4         1697792       918110207   437.0 GiB   0700  Gateway
   5         1435648         1691647   125.0 MiB   0C01  
   6       918110208      1450706943   254.0 GiB   8300  
   7      1450706944      1457928175   3.4 GiB     8300  

```
FYI my original screenshot (the one I am trying to recreate) was of an fdisk output and shows only 6 partitions.

---

### Post by oldfred on 2018-12-31
Your partition 5 shows as the msftres or Microsoft reserved.
And gdisk says this as description for its code:
0c01 Microsoft reserved

---

### Post by 1awc on 2019-01-02
Yes, but why is /dev/sdc5 appearing when it didn't before?  You said  that "most partition tools will not find it" and the original partition  was not found.  Why is it appearing now?

---

### Post by oldfred on 2019-01-02
Partition tools see it, but normally give error messages. 

If you look in gparted, it will have a yellow or red icon next to it. It really should not as it has a valid GUID that says it is the Microsoft system reserved & that has to be unformatted. Same with grub2's bios_grub partition. When I used BIOS to boot, gparted always complained about my bios_grub partition.

---

### Post by 1awc on 2019-01-05
I don't see anything like that. Nothing is booting so no errors or complaints.  Here is the current partition table.
[ATTACH=CONFIG]282102[/ATTACH]

  I get an error when using Gparted check on Sdd4. -- It has the most used space so I assume it is the most valuable.  When I mount the partitions with Disks, the fstab file is cleared when I reboot.

---

### Post by oldfred on 2019-01-05
Red icon with exclamation point is gparted saying there is an issue. But on your Microsoft system reserved that error is incorrect.

If you want to always mount a partition, you need to add it to fstab. But must make sure Windows fast start up is always off as if partition does not mount, boot may fail. Then you need your Windows repair disk & Ubuntu live installer to fix things.

       [https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by 1awc on 2019-01-08
Well this is worse than I ever thought it was.  I thought once the  partitions were restored I would be able to boot correct a few things  and be back to normal.  However, I am not able to boot, when I try  reinstall windows on the OS partition I am told that it is is closed,  when I try a reinstall I don't have the Product ID. 

 Testdisk isn't much help since the filenames are changed.

 The red icon with exclamation point says that it is too small (8KB) to  format as a swap, which I assume was the only productive thing to do  with it. 

 I am considering that perhaps when I took the first  screenshot my HDD it was already too messed up. After months of trying  to keep calm and avoid careless mistakes, I am reaching my limit. To top  it off, my 5 month old Sandisk 128GB USB which I was using to avoid  saving to HDD, has failed.

---

### Post by oldfred on 2019-01-08
Do not worry about 8KB that is tiny.

Windows has to be in UEFI boot mode to install in UEFI boot mode.  I would think if the fast start up or hibernation is set, Windows would still work with it, but you may need to use the repair function first to turn off the fast start up.

       Product key now in UEFI/BIOS, but if you attempt to install in BIOS mode it will not work
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by 1awc on 2019-01-10
I've tried both UEFI, Legacy, Secure enabled/disabled.

I've taken stock of what I have and so far I have/found:

backup xxxxxxx.PBF, BootUX (1).sqml 1-6, reload.xml, a family member's laptop with Windows 8 not yet updated to 8.1,

 FOLDER(1) 
bin
boot
dev
etc
home
lib
lib64
media
mnt
opt
proc
run
sbin
snap
srv
sys
tmp
usr
var

FOLDER(2) "ISO IMAGE of gateway et al" I made a USB boot from Folder(2) but will not boot. 
system
boot
boot.catalog
efi.img
mach_kernel

At this point I am think that making a recovery USB/disk from the Windows 8 laptop is my best option.  I will just consider myself lucky if I find the files haven't recovered with Photorec.

---

### Post by oldfred on 2019-01-10
Your folder(1) is the standard set of folders for Ubuntu as viewed from / (root).
Your user data & settings are normally in /home and then your user name. Settings may be hidden files, you have to turn on show hidden to see them. Setting files & folders start with a . , like .thunderbird

---

### Post by 1awc on 2019-01-12
I read your [[COLOR=Navy]UEFI boot install & repair [/COLOR]]("http://ubuntuforums.org/showthread.php?t=2147295")and I do have the files (bootx64.efi & shimx64.efi, and on some zip drive).  I ran Boot-repair again but I am still getting[ "The default repair of the Boot-Repair utility will not act on the boot."]("http://paste.ubuntu.com/p/bwrKT6JMSP/") Boot-repair is not repairing the boot.  I've run it several times.  It seems that I need to manually install the boot loader.  I will try that for awhile then attempt to reinstall Windows with the info/data borrowed from the functioning Win8 laptop.

I tried lilo but nothing changed.

---

