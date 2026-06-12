---
title: "unable to mount usb flash drive"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-11
I havee a 4 G Kingston usb drive. I think I have somehow busted it. 
When inserted I got an error message.
```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Runing dmesg | tail returned the following.

```


[  122.118139] sd 7:0:0:0: [sdc] No Caching mode page present
[  122.118145] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  122.121019] sd 7:0:0:0: [sdc] No Caching mode page present
[  122.121027] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  122.121759]  sdc: sdc1
[  122.123543] sd 7:0:0:0: [sdc] No Caching mode page present
[  122.123553] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  122.123560] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  122.335578] FAT-fs (sdc1): bogus number of reserved sectors
[  122.335584] FAT-fs (sdc1): Can't find a valid FAT filesystem

```

  A few months ago I cretaed a Fedora live usb with the dd command, which booted fine and I used it to install Fedora with no problem,. But then later I tried to use it for something else and reformatted it as vfat and it still mounted, then I tried to reformat it as ext 4 with gparted and the operation ended with an error and now it doesn't mount any more.

Just want to know if there is a way to save this drive, or do I have to buy a new one? Thanks.

---

### Post by FMFCorpsman on 2013-06-11
I'm new here, but my first question to you would be, is it formatted NTFS or Fat32? based on the dmesg it's looking for a FAT system

---

### Post by monkeybrain2012 on 2013-06-11
The last time it mounts was vfat. Then now it is nothing as I have deleted it from gparted but it failed to create an ext4 system.Never formatted as ntfs.

---

### Post by sudodus on 2013-06-12
I think you need to wipe it after the dd cloning. See this tutorial [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by monkeybrain2012 on 2013-06-12
Hi, thanks for the response, I should have wiped it like in your tutorial, but now it is not even mountable. Is there any way to fix it, or is it basically busted?

---

### Post by sudodus on 2013-06-12
You don't need and should not mount it. But it must be seen by for example fdisk -lu

---

### Post by monkeybrain2012 on 2013-06-19
Hi, sudodus,

Thanks for the help

I did
 ```
sudo dd if=/dev/zero bs=4096 of=/dev/sdc
```

Removed and reinserted the drive and run fdisk -l, which complained that the drive doesn't have a valid partition table, so I created one with gparted and reformatted it, it all works now.

What is bs=4096 and count=256?

I ran 

```
sudo dd if=/dev/zero of=/dev/sdc1
``` 

and it didn't work (i read a tutorial somewhere that the of is the partition (sdc1) rather than the drive (sdc))

Thanks again.

---

### Post by sudodus on 2013-06-19
/dev/sdc is the block device for the whole drive c
/dev/sdc1 is the block device for partition 1 on drive c

In such cases it is best to wipe the whole drive or at least the first megabyte to remove traces from the boot sector, partition table etc at the beginning of the drive.

bs is block size. I have found that in most cases 4096 B makes the copying faster than the default 512 B.
count is the number of blocks to copy. In this case the result is one megabyte (actually Mibibyte 1024x1024 B).

See ```
man dd
```

---

