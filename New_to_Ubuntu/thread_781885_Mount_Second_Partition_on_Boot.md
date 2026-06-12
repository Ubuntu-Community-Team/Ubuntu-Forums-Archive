---
title: "Mount Second Partition on Boot"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Picaroon on 2008-05-04
I am currently dual-booting and want to put all my photos, music, videos, etc. on a seperate partition that's accessible by both Ubuntu and Windows.

I have that partition but I do not have write access when I open it, and it does not mount on boot.

What do I need to put in fstab to make it mount on boot with write permissions for my user?

Here's my fdisk. The one I want to mount on boot is /dev/sda4. I already have drivers in Windows to read that partition.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64f164f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5100    20482875   83  Linux
/dev/sda3            5101        5161      489982+  82  Linux swap / Solaris
/dev/sda4            5162        9729    36692460   83  Linux

```

---

### Post by quirks on 2008-05-04
1. Open a terminal.

2. Create a directory where you want the partition to be mounted. For example:
```
sudo mkdir /shared
```
3. Determine the UUID of the partition you want to mount:
```
sudo tune2fs -l /dev/sda4 | grep UUID
```
Output should look similar to this:
```
Filesystem UUID:          79e5b078-1ba3-44ec-9e60-55ab19938161
```
3. Make a backup of /etc/fstab:
```
sudo cp -p /etc/fstab /etc/fstab~
```
4. Open /etc/fstab:
```
gksu gedit /etc/fstab
```
5. Add the following line to the file (make sure to use your UUID):
```
UUID=79e5b078-1ba3-44ec-9e60-55ab19938161 /shared           ext3    defaults        0       2
```
6. Save the file and reboot.

7. After reboot, check if it worked using the mount command:
```
mount
```
The partition should be listed somewhere.
```
/dev/sda4 on /shared type ext3 (rw)
```
8. Open a terminal and create a directory in the newly mounted partition, which your user is allowed to write to:
```
sudo mkdir /shared/*your_username*
sudo chown your_username /shared/*your_username*
```
9. Optionally, you might want to put a link on your Desktop or into your home directory, so that you can access the partition easily:
```
ln -s /shared/*your_username* ~/shared
```

That should do the trick. Tell me, if you have problems following these steps.

As a final note, I want to say that it would have been better, if you had separated your data and operating system by putting / and /home on two distinct partitions, where the /-partition is about 8GB and the /home-partition gets whatever is left. Then you wouldn't need to do all this now. However, setting up this would be even more complicated, now that you have already partitioned your hard disk this way.

---

### Post by Ducatiboy Stu on 2008-05-04
You should already be able to see your windows partition under the places menu. You may have to mount it by right-clicking on it

That way you can use the windows part without making a new one

---

### Post by bodhi.zazen on 2008-05-04
You can list your partitions by UUID with 

```
sudo blkid
```

Or

ls -l /dev/disk/by-uuid

---

