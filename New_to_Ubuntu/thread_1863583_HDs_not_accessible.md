---
title: "HDs not accessible"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by DrMilo on 2011-10-18
I am having trouble figuring out how to permanently have access to my hard drives, other than my mount point one, in Ocelot. They are all showing as mounted, but the files are not accessible. I get an error on boot up that they are not ready. 

I've had versions of this problem since Narwhal but since Ocelot, they seem to be particularly uncooperative. 

PySDM did not seem to solve my problem; it says:

mount: unknown filesystem type 'swap'
mount: unknown filesystem type 'swap'
mount: unknown filesystem type 'swap'
Traceback (most recent call last):
  File "pysdm.py", line 233, in on_partitiontree_cursor_changed
    if len(ptree.get_selection().get_selected_rows()[1][0])==1: 
IndexError: list index out of range
mount: unknown filesystem type 'swap'
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async
Warning: Unknown option: defaults

Thank you in advance for your help!

---

### Post by drofart on 2011-10-18
Are you sure you are looking at the right drive?  What's the output of this command from a terminal?

sudo fdisk -l

---

### Post by DrMilo on 2011-10-18
Here ya' go:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf964ce7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   958630679   479315308+  83  Linux
/dev/sda2       958630680   976768064     9068692+   5  Extended
/dev/sda5       958630743   976768064     9068661   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aca86

   Device Boot      Start         End      Blocks   Id  SystemDisk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf964ce7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   958630679   479315308+  83  Linux
/dev/sda2       958630680   976768064     9068692+   5  Extended
/dev/sda5       958630743   976768064     9068661   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aca86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   859943384   429971661   83  Linux
/dev/sdb2       859943385   976768064    58412340    5  Extended
/dev/sdb5       970711623   976768064     3028221   82  Linux swap / Solaris
/dev/sdb6       859943511   966100904    53078697   83  Linux
/dev/sdb7       966100968   970711559     2305296   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d653e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   476327249   238163593+  83  Linux
/dev/sdc2       476327250   488392064     6032407+   5  Extended
/dev/sdc5       476327313   488392064     6032376   82  Linux swap / Solaris

/dev/sdb1   *          63   859943384   429971661   83  Linux
/dev/sdb2       859943385   976768064    58412340    5  Extended
/dev/sdb5       970711623   976768064     3028221   82  Linux swap / Solaris
/dev/sdb6       859943511   966100904    53078697   83  Linux
/dev/sdb7       966100968   970711559     2305296   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d653e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   476327249   238163593+  83  Linux
/dev/sdc2       476327250   488392064     6032407+   5  Extended
/dev/sdc5       476327313   488392064     6032376   82  Linux swap / Solaris

---

### Post by Morbius1 on 2011-10-18
Please post the output of the following commands:
```
cat /etc/fstab
sudo blkid -c /dev/null

```

---

### Post by DrMilo on 2011-10-18
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                                      proc         defaults               0  0  
# / was on /dev/sda1 during installation
UUID=59ad7451-dd09-498e-acb0-d3c079912f70  /                                          ext4         defaults               0  1  
# swap was on /dev/sda5 during installation
# new ids
UUID=9f4f0622-8701-4921-bda4-cefabdca14bf  none                                       swap         defaults               0  0  
#                                          UUID=e4fadf58-8d56-41a9-a82e-26f54e787997  ext3         errors=remount-ro      0  1  
# UUID=18c253ed-1362-49cf-aa3b-1a2ded687a2a none           swap         sw                     0  0  
# UID=f34d1a04-d902-4a1b-af7e-88b5d315588e none ext4         errors=remount-ro      0  1  
# UUID=d8a057ee-00df-4560-acbd-821b565385dd none           swap         sw                     0  0  
# UUID=a2afc27a-3a36-4608-b35d-59f9fdc0ab5a none ext4         errors=remount-ro      0  1  
# UUID=5d1cb7b5-02ef-4f20-809f-474230e2c6ed none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0                              udf,iso9660  user,noauto,exec,utf8  0  0  
# /dev/sdb6                                  /media/sdb6    ext4         defaults               0  0  
/dev/sdc1                                  /media/sdc1                                ext4         defaults               0  0  
# /dev/sdb1                                  /media/sdb1    ext3         defaults               0  0  
# /dev/sdb5                                  /media/sdb5    swap         defaults               0  0  
/dev/sdb7                                  /media/sdb7                                swap         defaults               0  0  
/dev/sdc5                                  /media/sdc5                                swap         defaults               0  0  
/dev/sdc7                                  /media/sdc7                                swap         defaults               0  0  
/dev/sdc6                                  /media/sdc6                                ext4         defaults               0  0  
/dev/sdb1                                  /media/sdb1                                ext3         defaults               0  0  
/dev/sdb5                                  /media/sdb5                                swap         defaults               0  0  
/dev/sdb6                                  /media/sdb6                                ext4         defaults               0  0  


/dev/sda1: UUID="59ad7451-dd09-498e-acb0-d3c079912f70" TYPE="ext4" 
/dev/sda5: UUID="9f4f0622-8701-4921-bda4-cefabdca14bf" TYPE="swap" 
/dev/sdb1: UUID="e4fadf58-8d56-41a9-a82e-26f54e787997" TYPE="ext3" 
/dev/sdb5: UUID="18c253ed-1362-49cf-aa3b-1a2ded687a2a" TYPE="swap" 
/dev/sdb6: UUID="f34d1a04-d902-4a1b-af7e-88b5d315588e" TYPE="ext4" 
/dev/sdb7: UUID="d8a057ee-00df-4560-acbd-821b565385dd" TYPE="swap" 
/dev/sdc1: UUID="a2afc27a-3a36-4608-b35d-59f9fdc0ab5a" TYPE="ext4" 
/dev/sdc5: UUID="5d1cb7b5-02ef-4f20-809f-474230e2c6ed" TYPE="swap"

---

### Post by Morbius1 on 2011-10-19
You have an awful lot of swap partitions there. You only need one you know. Anyway, the only swap partitions that are defined in fstab correctly are the ones you commented out, for example:
> UUID=18c253ed-1362-49cf-aa3b-1a2ded687a2a none           swap         sw                     0  0  So change " swap defaults" in these:
> /dev/sdb7 /media/sdb7 swap defaults 0 0
/dev/sdc5 /media/sdc5 swap defaults 0 0
/dev/sdc7 /media/sdc7 swap defaults 0 0 
/dev/sdb5 /media/sdb5 swap defaults 0 0To this:
```
none           swap         sw
```You have another problem in that you have too many partitions on too many drives for pysdm to handle properly. It was discovered some time ago that depending on the "mood" of the BIOS when you boot partitions could "flip" ( sdb becomes sda for example ) so this will most likely cause a problem in time. THat's why you see partitions referenced by UUID numbers instead of the legacy /dev/sdxy way. Remember that Pysdm was written a long time ago and have been repackaged to run in current systems but has never been updated to reflect current standards.

---

### Post by DrMilo on 2011-10-19
> **Morbius1 said:**
> You have an awful lot of swap partitions there. You only need one you know. Anyway, the only swap partitions that are defined in fstab correctly are the ones you commented out, for example:
So change " swap defaults" in these:
To this:
```
none           swap         sw
```You have another problem in that you have too many partitions on too many drives for pysdm to handle properly. It was discovered some time ago that depending on the "mood" of the BIOS when you boot partitions could "flip" ( sdb becomes sda for example ) so this will most likely cause a problem in time. THat's why you see partitions referenced by UUID numbers instead of the legacy /dev/sdxy way. Remember that Pysdm was written a long time ago and have been repackaged to run in current systems but has never been updated to reflect current standards.

I appear to have been misled by rhythmbox too, it does not seem to find some music from my HDs that aren't the booting ones, even though they are accessible. I am the king of getting simultaneous errors that cause the same problem!

I suppose I should just redo the partitions, eliminating those swaps, they also generate error messages on startup that are annoying.

---

