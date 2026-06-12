---
title: "Partition...Partition!!"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-08-14
Hello

Still new to Ubuntu but learning fast!
OK.
How can I create another partition for my personnal files?
Very experimented with Windows but I have to "think Linux". Right?
Thanks.

Luc

---

### Post by Bashing-om on 2013-08-14
Luc_Lacombe; Hi !

Partitioning .. a piece of cake, nothing to it .. common sense rules !
These links will provide:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
bodhi.zazen's great tutorial.

Always: back up your data prior to doing anything - never can tell what might perchance.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by drgor on 2013-08-15
Hi,
If you are installing only ubuntu, I suggest this scheme

Create one ext4 partition with mount point "/", this is where your system files will go (20 GB should be fine), even less will do if you have older computer
One more partition for swap file (size equal to your RAM), type of partition will be swap area, no mount point
Last and largest will be your personal files/data, mark as "/home", all your data will be here. Use ext 4 only. Some function may fail with fat/ntfs (personal experience)

So when you are reinstalling ubuntu (in future), do not format /home partition and all your personal data will be saved.
If you are using dual boot with windows, you may keep one more parition in fat32/ntfs which may be used to install windows. However you have to install windows first and then ubuntu otherwise windows will overwrite grub.
You can also have one fat/ntfs partition for data which can be read by both windows and ubuntu. windows can not read ext4.

One harddisk can only have max. 4 primary partition. So if you need more use logical partitions

---

### Post by Luc_Lacombe on 2013-08-15
Hello drgor and Bashing-om

Thanks for helping me and sorry for the delay.
I have to give some precisions here.
I have to create a second partition to my HD for my personnal files.
I have to say I don't want to install any other OS on this computer.
 It's fully dedicated to Ubuntu and I have no intention to have M$ aside it!
This partition or even another one if needed would be used for temporary Ubuntu backups.
I would end with a system and two data files partitions...that means 3 partitions.
So with this in mind, am I on the rack track to follow your advices you both gave me in the preceeding posts?

By the way, how can we have sytem informations about hardwares and disks?
Don't forget...I'm a Windows "thinker" and slowly Linux learning!
Thanks again for your help!!

Luc

---

### Post by Bashing-om on 2013-08-15
Luc_Lacombe;
Commnad line tools to look at the disk(s):
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
##The indispensable manual installed on all linux systems !
##see:
man man
man fdisk
man parted

```
GParted is ubuntu's partition editor, available by default on ubuntu's install medium ..Takes a bit of reading and practice to become comfortable with the editor .. but in use ..is straight forward and easy to use.

hardware looksee:
```

lspci
lsusb
lshal
lshw
##for instance;
##To see your graphics card and info:
sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga 
lspci -vnn | grep -i VGA

```

An example of what a system lloks like after several rears using 'buntu:
> 
sysop@1304mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000945e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   968384511   484191232   83  Linux
/dev/sdc2       968386558   976771071     4192257    5  Extended
sysop@1304mini:~$ 

Same look from a different perspective:
> 
sysop@1304mini:~$ sudo parted -l
Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5244MB  5243MB  primary   ext4            boot
 2      5245MB  15.7GB  10.5GB  primary   ext4
 3      17.5GB  500GB   483GB   extended
 8      17.5GB  22.8GB  5243MB  logical   ext4
 5      227GB   227GB   8193kB  logical   linux-swap(v1)
 6      227GB   306GB   78.6GB  logical   ext4
 7      306GB   500GB   194GB   logical   ext4


Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext4


Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  496GB  496GB   primary   ext4         boot
 2      496GB   500GB  4293MB  extended


sysop@1304mini:~$ 


How one partitions their system is personal, depending on how and what the system is to be used for ...With time and experience one tends to re-partition several times to meet changing conditions and needs.
Just starting out .. may I offer this for the simplicity and the opportunity of a learning experience.
Install 'buntu ... pick a flavor of "ubuntu" or some other linux distro (hundreds)... -> "erase and use entire disk" option. 
Then: To make your data partitions, fire up GParted .. shrink the present "/" partition to say 50 Gigs - from the right tword left end.. leaving all to the remaining right end to partition into your "data" partitions. This space becomes "unallocated"
Right click on the unallocated space, select new .. set size, use as, format type (I suggest you stay with ext4) and give it a label ... 
Repeat to set up for additional partitions ... suggest ya leave 10 Gigs or so "unallocated" for future use.
from task bar menu choose "apply pending operations" ... confirm what it shows is what you really want .. and "Apply".

done !

Later on with gained knowledge and experience, you will set up all your various operating system partitions and data partitions before hand- prior to installing. By then you will be comfortable doing a "manual install".

On a fresh install ... playing around and making mistakes is acceptable ... All you are going to loose by having to (re-)install is a bit of time ...30 minutes or so ..Remember, it is simple, once you know how ...  do not make it more complicated than it is not ... 

[INDENT]above all, enjoy yourself
[/INDENT]

---

