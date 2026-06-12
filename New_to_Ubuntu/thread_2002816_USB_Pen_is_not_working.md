---
title: "USB Pen is not working"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by JLeite on 2012-06-13
I have a Lexar 32GB usb pen that doesn't work.
When I try to format it with Disk Utility I get:
[http://www.mediafire.com/i/?zk76jmsc4vvk5k2](http://www.mediafire.com/i/?zk76jmsc4vvk5k2)
GParted can't see the device.
Is there a way to fix this?
Thank you

---

### Post by oklokl on 2012-06-13
Your usb..
The position of the image is /dev/sdc is the ...

ctrl alt T

# Automatic Unmounting
```
 sudo umount -l /dev/sdc1
```Please clear the usb.
remove usb 
```
sudo dd if=/dev/zero of=/dev/sdc bs=446 count=1234
```Please create a new mbr.
 Nautilus is often an error.
# make mbr...
```
sudo parted /dev/sdc
``````
h
mklabel
msdos
p
mkpart
0
-1
q
```# How is the data format can be erased.
# format /dev/sdc1
```
sudo mkfs.ntfs -f /dev/sdc1
```# or ext4 
```
sudo mkfs.ext4 -L "1234" /dev/sdc1
```# badblock test..

```
sudo badblocks -vw /dev/sdc1
```

---

### Post by JLeite on 2012-06-13
Greetings.

When I type: 
 sudo umount -l /dev/sdc1
I get:
umount: /dev/sdc1: not found

I forgot to mention but I'm with Ubuntu 12.04

---

### Post by oklokl on 2012-06-13
No need to worry. (umount: /dev/sdc1: not found)
You is not mounted.
error..

When you automount
 Is unmount.
So that the partition can be formatted.
The message is normal. (umount: /dev/sdc1: not found)

Than that.
 usb drive, look at the position.

```
sudo parted -l
```or..

```
sudo fdisk -l
```This is also available.
 Hoksina your / dev/sdc if you have the rest of the partitions will be turned off.
```
sudo umount -l /dev/sdc[0-9]*
``````
sudo umount -l /dev/sdc1p[0-9]*
``````
sudo umount -l /dev/sdc2p[0-9]*
```and..
Try the other side to insert usb ..
will be inserted into the back of pc.

Try on another computer, insert the ...
 Test

If old usb
 Will cause compatibility problems.

---

### Post by JLeite on 2012-06-13
The output for 
sudo parted -l
is:

Model: ATA Maxtor 6V300F0 (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  300GB  300GB  primary  fat32        boot, lba


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  489GB  489GB   primary   ext4
 2      489GB   500GB  10.8GB  extended
 5      489GB   500GB  10.8GB  logical   linux-swap(v1)




And the output for 
sudo fdisk -l
is:

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fc7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   586099394   293049666    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000daffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   955594394   477797166   83  Linux
/dev/sdb2       955594395   976768064    10586835    5  Extended
/dev/sdb5       955594458   976768064    10586803+  82  Linux swap / Solaris

Finally, the output for: sudo umount -l /dev/sd[c-z][0-9]*
is:
umount: /dev/sd[c-z][0-9]*: not found

---

### Post by oklokl on 2012-06-13
If usb is inserted.
 umount the.
 Insert should not have usb or if you don `t recognize the commands are not needed.

```
sudo parted -l
```
Case of
/dev/sdc

If it's not recognized.
there is a problem with usb.

---

### Post by JLeite on 2012-06-13
Now, I'm a little confused. I should enter sudo parted -l with the pen inserted or not?
sudo parted -l gives me the drives in the machine and I have two HDD (sda and sdb) with the filesystem on sdb.

---

### Post by JLeite on 2012-06-14
Any new ideas?

---

### Post by Sylos on 2012-06-14
Hello.

with your pen drive inserted Try:

```
sudo mount
```
```
sudo fdisk -l
```

This should tell you everything that is mounted. You should see your pen drive near the bottom of the list. Depending on how many drives adn partitions you have it will be given different letter and number. It should be the last letter.

If it doesnt appear then it suggests drive death that I wouldnt know how to recover.

Cheers

EDIT: changed due to foolish suggestion.

EDIT2: was right the first time.

---

### Post by JLeite on 2012-06-14
Greetings, Sylos
The output for sudo mount is:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jleite/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jleite)

and the output for sudo fdisk -l is:
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fc7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   586099394   293049666    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000daffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   955594394   477797166   83  Linux
/dev/sdb2       955594395   976768064    10586835    5  Extended
/dev/sdb5       955594458   976768064    10586803+  82  Linux swap / Solaris



There's no mention to the pen..
Thank you for your contribution.

---

