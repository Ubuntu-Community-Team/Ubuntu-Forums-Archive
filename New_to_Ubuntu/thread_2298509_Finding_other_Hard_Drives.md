---
title: "Finding other Hard Drives"
date: 2015-10-11
forum: New to Ubuntu
---

### Post by crastopher on 2015-10-11
Hello,
Recently switched from W10. I have 3 hard drives, and can't seem to access two of them. One of them is a 1TB, and has a bunch of movies that I want to grab, so I can setup my Plex server again. Here is what I get from it when I fdisk -l:[/FONT]
```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes 256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 4096 bytes I/O size (minimum/optimal): 4096 bytes / 4096 bytes Disk identifier: 0x00000000
Device Boot Start End Blocks Id System /dev/sdc1 1 4294967295 2147483647+ ee GPT
```
How do I go about adding/mounting this?

---

### Post by crastopher on 2015-10-11
[FONT=verdana]Just tried the following:[/FONT]
[INDENT]sudo mount /dev/sdc /mnt
[/INDENT][FONT=verdana]and[/FONT]
[INDENT]sudo mount /dev/sdc
[/INDENT][FONT=verdana]I am receiving this message:[/FONT]
[INDENT]Failed to mount '/dev/sdc': Invalid argument The device '/dev/sdc' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/INDENT]

---

### Post by sandyd on 2015-10-11
Explanation of fdisk -l output:

```

Disk [COLOR="#800000"]/dev/vda[/COLOR]: [COLOR="#8B4513"]268.4 GB, 268435456000 bytes[/COLOR]
[COLOR="#2F4F4F"]255 heads, 63 sectors/track, 32635 cylinders, total 524288000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9c29[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
[COLOR="#0000FF"]/dev/vda1            2048   524287999   262142976   83  Linux[/COLOR]

```

[table="width: 500, class: grid"]
[tr]
	[td]Section[/td]
	[td]Description[/td]
[/tr]
[tr]
	[td][COLOR="#800000"]/dev/vda[/COLOR][/td]
	[td]This is a block device that provides access to your hardware. In this case, it is your hard disk[/td]
[/tr]
[tr]
	[td][COLOR="#8B4513"]268.4 GB, 268435456000 bytes[/COLOR][/td]
	[td]Capacity of the block device[/td]
[/tr]
[tr]
	[td][COLOR="#2F4F4F"]255 heads, 63 sectors/track, 32635 cylinders, total 524288000 sectors[/COLOR][/td]
	[td]This and the next few lines indicate a bit of info about the block device including the number of sectors and sector size[/td]
[/tr]
[tr]
	[td][COLOR="#0000FF"]/dev/vda1            2048   524287999   262142976   83  Linux[/COLOR][/td]
	[td]This line, and additional ones that may be below it refer to partitions on the device. The first column is the block device of the partition, the second column indicates if the boot flag is set. It isn't set on this partition, so there is just a blank space. The third/fourth column indicate the starting and ending positions of the partition. The fifth column indicates the number of blocks, and the sixth/seventh column indicates the partition identifier. If a line like this is absent, there are no partitions on the device. See below for exception.[/td]
[/tr]
[/table]

Note that if you get the following message in the fdisk -l output:
```

The util fdisk doesn't support GPT. Use GNU Parted
```

Use the command
```

parted -l
``` instead.

That being said, filesystems such as NTFS are stored on partitions. You can mount them with
```

sudo mount *block device* */mountpoint*
```

In the above output, you don't seem to have any partitions on the drive.

---

### Post by oldfred on 2015-10-11
You do not mount drives like sdc, but partitions like sdc1.
Is it NTFS?

If gpt partitioned do use parted or gdisk. Only the very new fdisk in 15.10 now supports gpt partitioned drives.

---

### Post by crastopher on 2015-10-11
So after a parted -l, I get:

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata


now, if I do sudo mount /dev/sdc2 /mnt, I get:

The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by yancek on 2015-10-12
Your last post shows that your partitions cannot be mounted because they are in an unsafe state.  You need to shut down windows as it hibernates by default and won't mount in Linux.  So you need to disable any reference to fastboot or hibernation as stated in the message you posted.

---

### Post by sandyd on 2015-10-12
Is that Windows 8 or 10?

If so, you need to ensure that

a) The system is not hibernated, Ubuntu cannot read hibernated disks
b) The system has fast startup disabled. See [https://sites.google.com/site/easylinuxtipsproject/windows#TOC-Disable-Fast-Startup-no-loss-it-s-misleading-anyway-](https://sites.google.com/site/easylinuxtipsproject/windows#TOC-Disable-Fast-Startup-no-loss-it-s-misleading-anyway-) for instructions.

---

### Post by crastopher on 2015-10-12
That worked! Thank you!

Now, to clear up some confusion... Is the /mnt folder now going to be solely that hard drive? Can I rename it?

---

### Post by sandyd on 2015-10-12
> **crastopher said:**
> That worked! Thank you!

Now, to clear up some confusion... Is the /mnt folder now going to be solely that hard drive? Can I rename it?

You can mount it anywhere you like.

Just unmount it 
i.e.
```
sudo umount /mnt
```
and you can move it somewhere else

Mounting another drive inside /mnt while a drive is already mounted in /mnt can be done as well though you probably won't want to do so under normal circumstances.

---

### Post by mastablasta on 2015-10-12
the drive should also be visible in the file manager and would auto mount when you click on it. as long as it is not in "unsafe state". so if you fixed that part you should be good to go in GUI.

---

