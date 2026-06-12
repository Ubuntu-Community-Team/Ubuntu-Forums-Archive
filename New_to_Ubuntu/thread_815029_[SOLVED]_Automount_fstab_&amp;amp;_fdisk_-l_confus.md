---
title: "[SOLVED] Automount: fstab &amp;amp; fdisk -l confusion"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by mherrin on 2008-06-01
Hi I've had a scan through the forums & Googled about this, but there seems to be a potentially hazardous discrepancy here, so I'd better ask...

System: 
Hardy 8.04 Ubuntu AMD64.
2x SATA disk drives
1x IDE Disk
1x DVDRW (IDE)

I am using the system fine, and enjoying it - however I (like a lot of other beginners) am having a struggle automounting a partition.

I have created a mount point /home/everyone
I can "sudo mount /dev/sdb /home/everyone

However whilst looking into editing the /etc/fstab I noted a discrepancy between the contents of this file & fdisk -l (both listed below)

before creating a new line in fstab I'd like a little reassurance I'm not going to shaft my system... ;-)

[COLOR="DarkGreen"]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    5  Extended
/dev/sda5   *           1          48      385497   83  Linux
/dev/sda6              49        1918    15020743+  83  Linux
/dev/sda7            1919        2300     3068383+  83  Linux
/dev/sda8            2301        2682     3068383+  83  Linux
/dev/sda9            2683        4594    15358108+  83  Linux
/dev/sda10           4595       38403   271570761   83  Linux
/dev/sda11          38404       38913     4096543+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000da121

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x95a87919

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         276     2086528+   6  FAT16
/dev/sdc2             277       20673   154201320    f  W95 Ext'd (LBA)
/dev/sdc5             277        2457    16488328+   7  HPFS/NTFS
/dev/sdc6            2458        5333    21742528+   7  HPFS/NTFS
/dev/sdc7            5334        5816     3651448+   7  HPFS/NTFS
/dev/sdc8            5817       20673   112318888+   7  HPFS/NTFS

[/COLOR]



[COLOR="Navy"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=24b94f98-b03e-40fb-9232-9cc78ab12558 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=b9a6f130-146c-459c-a2a2-e5095fa176a6 /boot           ext3    relatime        0       2
# /dev/sdb10
UUID=1eebc0b5-6866-4dc6-ab9f-2d69067ddec0 /home           ext3    relatime        0       2
# /dev/sdb7
UUID=8e83a8fd-5e2b-473d-a864-9704848c2f7e /tmp            ext3    relatime        0       2
# /dev/sdb9
UUID=0a69451d-be80-41cc-94f8-9525e0a4a7a1 /usr            ext3    relatime        0       2
# /dev/sdb8
UUID=e1eb6815-91e3-498b-a2c2-87f48186160e /var            ext3    relatime        0       2
# /dev/sdb11
UUID=b90bfae8-887c-499d-8f3b-3b5011d44a8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/COLOR]

Is this enough information to be going on with?
Is there any reason the two don't tally?
Can it be fixed readily?

I do have at least 2 copies of all the data on my system, but would rather not mess about re-installing, as I only did that last weekend.

TIA
Mike.

---

### Post by powerpleb on 2008-06-01
Why do you have so many partitions?

What's the output of this:
```
sudo mount -l
```
and
```
df
```

This may also help: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by mherrin on 2008-06-01
I have several versions of Windows that I run (ran ;-) ) on one disk.
1. for Work
2. For testing
3. For games
Then I had partitions for my data, my wifes' data and network share data.

This way I could "protect" Windows from slowing down, and restore backups of one Windows copy from another.

Also, I have separate Ubuntu partitions  / /home /tmp /var /usr swap /boot

It may not be everyones' taste, but it works well for me.

*unless of course, that's part of the problem*

Cheers,
Mike.

---

### Post by powerpleb on 2008-06-01
> **mherrin said:**
> 

Also, I have separate Ubuntu partitions  / /home /tmp /var /usr swap /boot

It may not be everyones' taste, but it works well for me.

*unless of course, that's part of the problem*


I don't think so. But in the fsck (pass) column they should either have different values or 0, especially if they are the same disk. Put them in order 1,2,3,etc

---

### Post by sisco311 on 2008-06-01
There is nothing wrong with your fstab.

The device name sda, sdb and sdc can alter when you reboot.
For example now:
sda = linux disk
sdb = linux data disk
sdc = windows disk

after reboot

sda = windows disk
sdb = linux disk
sdc = linux data disk

The partitions in fstab are mounted by UUID. UUID is an unique identifier for a partition.

To get the uuid of a partition:
```
sudo blkid /dev/sdb1
```

---

### Post by mherrin on 2008-06-02
Thanks for the replies, I'll have a go in a bit at changing the fstab.

BTW, it's [COLOR="Red"]blkid[/COLOR] (not bklid) - I thought I didn't have it installed until I googled the command with UUID in the search, too.

Will post back when I have had a go @ this.

Regards,
Mike.

---

### Post by sisco311 on 2008-06-02
Sorry for my typo.

---

### Post by mherrin on 2008-06-02
No Wukkas.

Here's what I've done to get it all working OK. I also added stuff for an NTFS partition.

I used a couple of GUI tools to see what they did, then made a few changes. The tools I used were ntfs-config and storage device manager.

They both added inconsistencies from the original fstab, which I edited out.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                                 0  0  
# Entry for /dev/sda6 :
UUID=24b94f98-b03e-40fb-9232-9cc78ab12558  /               ext3         relatime,errors=remount-ro               0  1  
# Entry for /dev/sda5 :
UUID=b9a6f130-146c-459c-a2a2-e5095fa176a6  /boot           ext3         relatime                                 0  2  
# Entry for /dev/sda10 :
UUID=1eebc0b5-6866-4dc6-ab9f-2d69067ddec0  /home           ext3         relatime                                 0  2  
# Entry for /dev/sda7 :
UUID=8e83a8fd-5e2b-473d-a864-9704848c2f7e  /tmp            ext3         relatime                                 0  2  
# Entry for /dev/sda9 :
UUID=0a69451d-be80-41cc-94f8-9525e0a4a7a1  /usr            ext3         relatime                                 0  2  
# Entry for /dev/sda8 :
UUID=e1eb6815-91e3-498b-a2c2-87f48186160e  /var            ext3         relatime                                 0  2  
# Entry for /dev/sda11 :
UUID=b90bfae8-887c-499d-8f3b-3b5011d44a8a  none            swap         sw                                       0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                    0  0  
# Entry for /dev/sdb1 :
UUID=377a33d8-e0a8-4a81-820f-9ebc1768e7a5  /home/everyone  ext3         errors=remount-ro                        0  0  
#/dev/sdc8
UUID=D06C37FA6C37D9C4                      /home/video     ntfs-3g      defaults,locale=en_GB.UTF-8,gid=everyone             0  0

---

