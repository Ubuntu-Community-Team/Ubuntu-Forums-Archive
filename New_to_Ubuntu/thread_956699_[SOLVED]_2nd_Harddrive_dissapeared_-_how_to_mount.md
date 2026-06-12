---
title: "[SOLVED] 2nd Harddrive dissapeared - how to mount?"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-23
I feel like a hypochondriac around these parts, but since my issues per my other posts, my second HD has dissapeared. Hmm.

It's in fdisk -l
```
joey@joey-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148604   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x682a8121

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156286976    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7087ef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

but when i run
```
joey@joey-desktop:~$ mount /dev/sdb1
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

```

Hmm. How do i fix this? I've done a clean shut down since.

---

### Post by WRDN on 2008-10-23
Ensure it is unmounted by typing:

```
sudo umount /dev/sdb1
```

Now, create the mount point:

```
sudo mkdir /media/disk
```

You can replace the word "disk" if you wish.

Finally, mount the disk:

```
sudo mount /dev/sdb1 /media/disk
```

---

### Post by Duck2006 on 2008-10-23
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by joey-elijah on 2008-10-23
Hey, thanks! That worked!

---

