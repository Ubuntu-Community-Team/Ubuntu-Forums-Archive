---
title: "Ext3 Resize issue... Plz help!!"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by awais_rauf on 2008-05-19
I had a 7 GB Ext3 partition on which i installed Ubuntu Hardy Heron. As I added more programs i needed more space on Ubuntu partition so I resized my NTFS partition and added 15GB space to the begining of Ext3 partition using Paragon Partition Manager ( a windows utility). But when i booted Ubuntu again the filesystem size was the same (7 GB) and not increased as i thought it would. Now when i check the size on any partition manager it tells me that there is a 22GB Ext3 partition but on checking the filesystem sze from ubuntu it is 7GB.

Can anyone please tell me how to grow the filesystem up to the partition size.

=======================================================================
Below are the output of fstab and df 
=======================================================================

-------------------------- **_/etc/fstab_**---------------------


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c641164d-8ed7-4cf4-8068-68436a855409 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=486cb6cb-2e46-44fc-8096-c16df7b8ccb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


--------------------------------**_ df -h _**---------------------

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.1G  6.4G  412M  95% /
varrun                252M  144K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   48K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   38M  214M  15% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      7.1G  6.4G  412M  95% /home/awais/.gvfs
/dev/scd0             700M  700M     0 100% /media/cdrom0
/dev/sda2              15G   65M   15G   1% /media/disk

---

### Post by Paqman on 2008-05-20
That sounds a bit odd. Can you please post the output of:
```

sudo fdisk -l

```

---

### Post by sdennie on 2008-05-20
If you've used a non-linux partition manager to change things, it almost certainly didn't know how to grow the ext3 filesystem after the partition that it lived on was resized.  What I would recommend doing is getting your Ubuntu install CD (the live CD) and booting up with that.  Once it's started, you should be able to run gparted on your disk and properly sort things out.

---

