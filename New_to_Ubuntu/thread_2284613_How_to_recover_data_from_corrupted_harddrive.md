---
title: "How to recover data from corrupted harddrive"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by Sarvagya on 2015-06-30
I have a Dell Inspiron 7520 laptop with 1TB inbuilt hardrive. Earlier it was showing some errors of failed sectors, which I ignored. But now the harddrive is corrupted and even windows is nto booting up. When I am trying to switch on my laptop it is just showing "media failure".

So now I am trying to recover my data by booting into ubuntu via usb.

Now I am booted into ubuntu but when I am trying to access my harddrive partitions it is showing this error :

"Error mounting /dev/sda9 at /media/ubuntu/502CCC6E2CCC50A0: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda9" "/media/ubuntu/502CCC6E2CCC50A0"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda9': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

I checked my partitions with "sudo parted -l" command. It showed all my partitions : 

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10JPVT-75A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  525MB   524MB   fat32        EFI system partition          boot, esp
 2      525MB   567MB   41.9MB  fat32        Basic data partition          hidden
 3      567MB   701MB   134MB                Microsoft reserved partition  msftres
 4      701MB   1215MB  514MB   ntfs         Basic data partition          hidden, diag
 5      1215MB  323GB   321GB   ntfs         Basic data partition          msftdata
 6      323GB   323GB   367MB   ntfs                                       hidden, diag
 7      323GB   323GB   367MB   ntfs                                       hidden, diag
 8      323GB   699GB   376GB   ntfs         Basic data partition          msftdata
 9      699GB   990GB   291GB   ntfs         Basic data partition          msftdata
10      990GB   1000GB  10.2GB  ntfs         Microsoft recovery partition  hidden, diag


Model: SanDisk USB Flash Drive (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot, lba



I am new to ubuntu. Please guide me how to mount my drives and recover the data.

---

### Post by sandyd on 2015-06-30
Before you continue, I _highly_ reccomend you create a backup using dd or ddrescue before you continue incase your disk fails mid recovery. The commands below may cause data loss due to the unclean windows filesystem. If you continue without backing up, files that you can't find are gone.

Try the following:

```

sudo ntfsfix /dev/sda9

```

If it still doesn't work, try
```
 
sudo ntfsfix -d /dev/sda9
```

---

### Post by Sarvagya on 2015-06-30
> **sandyd said:**
> Before you continue, I _highly_ reccomend you create a backup using dd or ddrescue before you continue incase your disk fails mid recovery. The commands below may cause data loss due to the unclean windows filesystem. If you continue without backing up, files that you can't find are gone.

Try the following:

```

sudo ntfsfix /dev/sda9

```

If it still doesn't work, try
```
 
sudo ntfsfix -d /dev/sda9
```

It worked like a charm. Now I am able to access all my partitions. I will backup my data immediately
Thanks a lot..

---

### Post by tgalati4 on 2015-07-01
You can marked this thread as SOLVED, by using Thread Tools.  Additional reading on data recovery:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

