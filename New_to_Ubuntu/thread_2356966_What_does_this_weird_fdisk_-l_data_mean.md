---
title: "What does this weird fdisk -l data mean?"
date: 2017-03-28
forum: New to Ubuntu
---

### Post by jmartino on 2017-03-28
Hi guys!


[LIST=1]
[*]I'm brand new to Ubuntu/Linux/Unix/etc.
[*]Really don't know what I'm doing but trying to learn.
[*]Ordered a new webserver last night.
[*]As soon as it was delivered I started Putty-ing around to see what I got.
[*]*"sudo fdisk -l"* provides the following output.
[*]I'm concerned because I'm not sure this server is what I ordered.
[*]I ordered **16GB RAM** with **(4) 1TB Drives set in a HW RAID-10**.
[*]Does the following look right to you?
[/LIST]

Note: The thing is... I setup this server with Serverpilot.io and it's saying that my "fullest disk" is already 42% and I haven't done anything with this server yet.

Thanks for looking!

```
root@server1:~# sudo fdisk -lDisk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 1.8 TiB, 2000342441984 bytes, 3906918832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5ae49ff0


Device     Boot      Start        End    Sectors  Size Id Type
/dev/sda1  *          2048     487423     485376  237M 83 Linux
/dev/sda2           489470 3906918399 3906428930  1.8T  5 Extended
/dev/sda5           489472 3906729983 3906240512  1.8T 83 Linux
/dev/sda6       3906732032 3906918399     186368   91M 82 Linux swap / Solaris
```

---

### Post by Dennis N on 2017-03-28
The first are ram disks. Explained here:
[http://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15](http://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15)
Followed by output for the regular physical disks.

---

### Post by Impavidus on 2017-03-28
You have a 237MB partition, which is probably a /boot partition. It would be about right that it's 42% full after installation. 237MB is not very large for a /boot partition, but is workable. No general data will be stored there, just the files the server needs to boot. It may fill up after a few kernel updates, so uninstall the old kernels. I think this can be done automatically nowadays.

---

### Post by jmartino on 2017-03-28
> **Dennis N said:**
> The first are ram disks. Explained here:
[http://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15](http://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15)
Followed by output for the regular physical disks.
Sweet Dennis. Thank you for that. I'd never heard that term,"RAM disk" before. Now it makes sense.

---

### Post by jmartino on 2017-03-28
> **Impavidus said:**
> You have a 237MB partition, which is probably a /boot partition. It would be about right that it's 42% full after installation. 237MB is not very large for a /boot partition, but is workable. No general data will be stored there, just the files the server needs to boot. It may fill up after a few kernel updates, so uninstall the old kernels. I think this can be done automatically nowadays.
Thanks Impavidus.  Boot partition makes perfect sense.  I just wish they'd made it a little bigger when they setup my server.  As you said, 237MB does seem rather small.  Also wish that Serverpilot was reporting the main disk volume, not the boot disk.

So am I correct in thinking that other plugins (like ImageMagick and AutoMySQLBackup) will be automatically stored in that boot partition since they are installed via SSH/root?  If so, I'm thinking I should figure out how to adjust that partition size a bit.

---

### Post by &amp;KyT$0P# on 2017-03-28
> **jmartino said:**
> So am I correct in thinking that other plugins (like ImageMagick and AutoMySQLBackup) will be automatically stored in that boot partition since they are installed via SSH/root?
Likely not, but I'm not 100% sure.  In order to be sure, please post the output of the following command -
```
df -hT
```

---

### Post by jmartino on 2017-03-28
> **halogen2 said:**
> Likely not, but I'm not 100% sure.  In order to be sure, please post the output of the following command -
```
df -hT
```
Cool.  Thanks for helping me!  Here's the data you requested. 

 As I'm looking at it, I realize how much I don't understand about this stuff.  I get that /dev/sda1 appears to be the boot partition and /dev/sda5 seems to be the 'usable' part of the drive.  Don't know what the rest means.  And it seems odd to me that it's sda1 and sda5 -- not sda1 and sda2.

```
root@nc1:~# df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.9G     0  7.9G   0% /dev
tmpfs          tmpfs     1.6G  9.0M  1.6G   1% /run
/dev/sda5      ext4      1.8T  2.7G  1.7T   1% /
tmpfs          tmpfs     7.9G     0  7.9G   0% /dev/shm
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1      ext2      230M   95M  123M  44% /boot

```

---

### Post by &amp;KyT$0P# on 2017-03-28
Thanks, that confirms that sda1 is indeed your [FONT=Courier New]/boot[/FONT] partition.

> **jmartino said:**
> So am I correct in thinking that other plugins (like ImageMagick and AutoMySQLBackup) will be automatically stored in that boot partition since they are installed via SSH/root?
Nope, they should go entirely into your [FONT=Courier New]/dev/sda5[/FONT] partition.  Installing software via SSH/root won't have an effect on that.

The only way you would automatically store anything in that boot partition is if you're installing a package that puts files in [FONT=Courier New]/boot[/FONT].  Imagemagick does not.  Nor should that type of software need to.

> **jmartino said:**
> Don't know what the rest means.
Anything saying "tmpfs" is dynamically generated by the system.  And thus can be safely ignored for this purpose.

That leaves the stuff you do understand. :)

> And it seems odd to me that it's sda1 and sda5 -- not sda1 and sda2.
Well, your sda2 partition is a logical volume group, not "just" a single partition.  That might have something to do with why you have no sda3 or sda4, but I don't know the details on that, sorry.

---

### Post by Dennis N on 2017-03-28
> it seems odd to me that it's sda1 and sda5 -- not sda1 and sda2.

You have MBR partitioning. It has up to 4 primary partitions, or can have 3 primary with 1 "extended" partition. Numbers 1-4 are reserved for these, even if you have fewer.

Extended partition is a container of more parititions, called logical partitions. As many as you can fit are allowed. Logical partitions are always numbered 5,6,...

If the next new partition you create is set as "primary" it will be numbered sda3. If you set it as "logical" it will be numbered sda6.

---

### Post by jmartino on 2017-03-29
Hi halogen2 and Dennis N.

I really appreciate you guys.  This makes a lot more sense to me now, and I'm more at ease with my setup.

Thank you!

I guess the only other question I have is... do you know of a way to monitor the health of the individual HDDs?  Evidently, my drives so not support S.M.A.R.T. reporting.  I just learned about smartmontools -- managed to install it -- but the output is:

```

root@server1:~# sudo smartctl -x /dev/sda5

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-64-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               HP
Product:              LOGICAL VOLUME
Revision:             6.60
User Capacity:        2,000,342,441,984 bytes [2.00 TB]
Logical block size:   512 bytes
Rotation Rate:        15000 rpm
Logical Unit id:      0x600508b1001cbd2a15c75fa18654efae
Serial number:        PACCP9SZ2JRB
Device type:          disk
Local Time is:        Wed Mar 29 10:33:22 2017 MST
SMART support is:     Unavailable - device lacks SMART capability.
Read Cache is:        Disabled
Writeback Cache is:   Disabled


=== START OF READ SMART DATA SECTION ===


Error Counter logging not supported


Device does not support Self Test logging
Device does not support Background scan results logging



```

I'm guessing this is a result of /dev/sda5 being a RAID 10 volume, and not a standalone drive.  Surely there's some way to proactively monitor the physical disks so that I know if/when one of them fails. (?)

As it stands now I don't even know how old the disks are.  They could be 10 years old for all I know.

---

