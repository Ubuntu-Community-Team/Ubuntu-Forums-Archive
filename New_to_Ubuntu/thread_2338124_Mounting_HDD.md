---
title: "Mounting HDD"
date: 2016-09-24
forum: New to Ubuntu
---

### Post by nickstaroba on 2016-09-24
I have a hard drive that was removed from an old  WD MyCloud device. This was a NAS one generation before they actually  started calling it MyCloud if that makes any difference.
  
I was told I should try reading the drive from Ubuntu so I'm running it from a USB.

This is my first time using Ubuntu and I'm fairly new to the command line...

When I plug the HDD in via my USB dock, I get this error:

```

Error mounting /dev/sdc4 at /media/ubuntu/20145d03-d3ec-44c2-a34d-62bd8425627b: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc4" "/media/ubuntu/20145d03-d3ec-44c2-a34d-62bd8425627b"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc4,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

  


When I run sudo fdisk -l


  ```

Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F718FA58-0B61-4964-A0A9-EA92BEB92ACE


  Device       Start        End    Sectors  Size Type
/dev/sdc1  1032192    5031935    3999744  1.9G Linux RAID
/dev/sdc2  5031936    9031679    3999744  1.9G Linux RAID
/dev/sdc3    30720    1032191    1001472  489M Microsoft basic data
/dev/sdc4  9031680 3907028991 3897997312  1.8T Microsoft basic data


```  
When I run sudo parted -l


  ```

Model: ASMT 2105 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


  Number  Start   End     Size    File system  Name     Flags
 3      15.7MB  528MB   513MB                primary  msftdata
 1      528MB   2576MB  2048MB  ext3         primary  raid
 2      2576MB  4624MB  2048MB  ext3         primary  raid
 4      4624MB  2000GB  1996GB  ext4         primary  msftdata


```


When I run sudo mount -t ext3 /dev/sdc4

```
mount: can't find /dev/sdc4 in /etc/fstab
```


Any suggestions? Thanks

---

### Post by Bucky Ball on 2016-09-25
Welcome. You've left out some info. Which Ubuntu and flavour of it are you using and do you have it installed or are you running a live session from the install media?

Are you looking to save the data on the drive to somewhere else or wipe it and reuse the drive for something else? Please include all relevant info to get support more quickly.

So far, what we do know is that the drive was used for, or as part of, a RAID array.

PS: What are you trying to mount the partition to with the command that threw this command?

```
mount: can't find /dev/sdc4 in /etc/fstab
```

Are you trying to mount it to anywhere??? Anyway, all you need to do is create a mount point:

```
sudo mkdir /mnt/data
```

... for instance, then mount it:

```
sudo mount /dev/sdc4 /mnt/data
```

... and sdc4 will be mounted in /mnt/data. You can deal with permission later if you need to.

---

