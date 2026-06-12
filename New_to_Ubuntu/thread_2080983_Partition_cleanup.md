---
title: "Partition cleanup"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by Toschano on 2012-11-05
0     down vote          [favorite]("http://askubuntu.com/questions/210684/uninstalling-12-10#")            
                                     What is the procedure to entirely remove Ubuntu 12.10?  I was  running Ubuntu 12.04 successfully and was advised that 12.10 was  available as an upgrade.  I updated 12.04 to 12.10 through the update  manager.  12.10 has been a pain in the a$$ to run from day 1.  I  installed a fresh copy of 12.04 to run alongside 12.10 on a seperate  partition.  I am a newbie at this and need to be able to clean the  hardrive (system?)of all except the new 12.04 and its files.   I've included the screen shot of my partitions from Gparted.  I would like to know which partitions I can remove  and how to go about it and possibly being able to save some files from the conversion.  I would think that if this  program is this buggy it shouldn't be offered as an update!!  Right now  I would  just  like to clean things up.  Any help would be appreciated in this matter.

---

### Post by ajgreeny on 2012-11-05
Your screenshot is missing!

However, please show the output of ```
sudo fdisk -l
sudo blkid -c /dev/null
mount
cat /etc/fstab
```from your current 12.04 and it may be possible to work out what is what and tell you which partitions you can remove.

---

### Post by Toschano on 2012-11-05
Thank you for your response...here are the results in Terminal...


elvio@elvio-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000643b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   276904713   138451333   83  Linux
/dev/sda2       276905982   488396799   105745409    5  Extended
/dev/sda5       486305792   488396799     1045504   82  Linux swap / Solaris
/dev/sda6       276905984   486305791   104699904   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              38     7839719     3919841    b  W95 FAT32
elvio@elvio-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="f3adcc00-da6f-4e9e-aba0-87bed0afb469" TYPE="ext4" 
/dev/sda5: UUID="5b9d634d-7d16-4e68-ac01-e75c37e9b100" TYPE="swap" 
/dev/sda6: UUID="ad795559-60de-40fd-b3ce-9adfaa9410ab" TYPE="ext4" 
/dev/sdc1: LABEL="PENDRIVE" UUID="B821-A605" TYPE="vfat" 
elvio@elvio-desktop:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/elvio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=elvio)
/dev/sda1 on /media/f3adcc00-da6f-4e9e-aba0-87bed0afb469 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
elvio@elvio-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ad795559-60de-40fd-b3ce-9adfaa9410ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5b9d634d-7d16-4e68-ac01-e75c37e9b100 none            swap    sw              0       0

---

### Post by dannyboy79 on 2012-11-05
from what I can see, your 12.04 install runs on /dev/sda6. so technically you should be able to use gparted from a live cd and delete /dev/sda1 and then grow /dev/sda6 to include that space where 12.10 used to be.

Now when you boot into a live cd, it may not be /dev/sdaX anymore, it may be /dev/sdbX, the important part is that the 1st partition on your 250GB hard drive is the one with 12.10 on it which can be deleted as you say.

Good luck

---

### Post by Toschano on 2012-11-05
Thanks a lot...one last question...is there anything I should back up and with what?

---

### Post by ajgreeny on 2012-11-06
YES, YES, YES !!

Always back up before you carry out any partition editing, even if you are not changing the partitions with your files and OS on.  I have never had a problem using gparted personally, but it is too easy, particularly for someone new to dealing with partitions, to click on the wrong partition and then find you've wiped the wrong one.  It is also not impossible for gparted to go wrong, or a power failure to cause corruption of the partition table.

How best to do a backup?  There are many options.  I just use rsync with a USB external drive to regularly back up my /home, but there are other ways; burn to DVD/CD if you've not too much data, use USB flash drives, run deja-dup, etc etc.  I never bother with the OS itself as that can be easily replaced, but my own data files are irreplaceable, so that's what I backup.

---

### Post by omerderi on 2012-11-06
I believe "Remastersys" is a better way of backing up Ubuntu. 

Using it you can make a full backup of your system icluding the latest updates and software that you've installed, and you can create a Live and 'installable' OS on a USB flash disk from your installed distro..

It is available for download via 'Synaptic'..

for more information read this:

[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)

---

### Post by ajgreeny on 2012-11-06
> **omerderi said:**
> I believe "Remastersys" is a better way of backing up Ubuntu. 

Using it you can make a full backup of your system icluding the latest updates and software that you've installed, and you can create a Live and 'installable' OS on a USB flash disk from your installed distro..

It is available for download via 'Synaptic'..

for more information read this:

[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)
Not so easy if you've got 100GB or more in /home, as I have, and I think it is so easy to re-install Ubuntu that, as I said, I don't bother to backup my OS, just my /home.

But you're correct that remastersys is another possibility, as is clonezilla.

---

