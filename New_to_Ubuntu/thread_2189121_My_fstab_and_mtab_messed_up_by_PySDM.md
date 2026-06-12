---
title: "My fstab and mtab messed up by PySDM"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by grldfry on 2013-11-20
I can't mount my second and third hard drives any more. They were messed up using Storage Device Manager (PySDM). I gather I need to modify / edit my fstab and/or mtab but have no idea what to do. Here is some info that may help tell me how to fix it.
I get this when trying to mount either of them:
mount error

```
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
```

 I also have this info:
 ```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ec974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    75020287    37509120   83  Linux
/dev/sda2        75022334    78163967     1570817    5  Extended
/dev/sda5        75022336    78163967     1570816   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20019314176 bytes
255 heads, 63 sectors/track, 2433 cylinders, total 39100223 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae3f1

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b683053

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625142447   312571192+  83  Linux

```

and this:
```
sudo blkid

/dev/sda1: UUID="e0e89aaa-feea-4880-8052-95ba8d98ae90" TYPE="ext4" 
/dev/sda5: UUID="b5f7ed26-03cb-4cd8-b865-d09ef3d6caba" TYPE="swap" 
/dev/sdc1: LABEL="Storage 320" UUID="72af2006-e764-45c8-8830-6d8bc887f08f" TYPE="ext4" 
/dev/sdb1: LABEL="storage 20" UUID="4b06688f-61a7-4a3a-985c-93fb60a48fcb" TYPE="ext4" 

```

and this is the fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=e0e89aaa-feea-4880-8052-95ba8d98ae90  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=b5f7ed26-03cb-4cd8-b865-d09ef3d6caba  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb                                   /media/storage 20   ext4  defaults                  0  0  
/dev/sdc1                                  /media/Storage 320  ext4  defaults                  0  0  
/dev/sdc1                                  /media/Storage 320  ext4  defaults                  0  0  
/dev/sdc1                                  /media/storage 20  ext4  defaults                  0  0  
/dev/sdc1                                  /media/sdc1     ext4  defaults                  0  0  

```

 and this is fstab.bak
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=e0e89aaa-feea-4880-8052-95ba8d98ae90  /               ext4  defaults                  0  1  
# swap was on /dev/sda5 during installation
UUID=b5f7ed26-03cb-4cd8-b865-d09ef3d6caba  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb                                   /media/storage 20   ext4  defaults                  0  0  
/dev/sdc1                                  /media/Storage 320  ext4  defaults                  0  0  
/dev/sdc1                                  /media/Storage 320  ext4  defaults                  0  0  
/dev/sdc1                                  /media/storage 20  ext4  defaults                  0  0  
/dev/sdc1                                  /media/sdc1     ext4  defaults                  0  0  

```

I hope this is enough info to help me fix this. I am totally lost with using ubuntu or any type of linux as I just recently switched from that overpriced OS from MS. I used different colors to separate the information, hope it helps. Thanks.

---

### Post by oldfred on 2013-11-20
Post this also:
cat /etc/fstab    

Also the spaces in labels may be an issue. Linux does not like spaces and you have to quote or escape the space character to use the label anywhere. Better to use CamelCase, under_score or justonelabel.

Almost all of the gui fstab editor do not work well. 
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

