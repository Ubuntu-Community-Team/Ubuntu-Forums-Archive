---
title: "unknown file system type '1'"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by kling on 2012-03-30
I'm running Ubuntu 11.10 and when I reboot I receive the following error:

mount:  unknown filesystem type '1'
mountall:  mount 0 [304]terminated with status 32
mountall: Filesystem could not be mounted: 0
fsck from util-linux 2.19.1
/dev/mapper/mail1-root:  clean,75841/4194304 files, 662535/16773120 blocks
/dev/sda1:  clean, 229/124496 files, 39604/248832 blocks 
An error occurred while mounting 0.
Press S to skip mounting or M for manual recovery

If I press S to skip, system seems to continue and I can log in.  If I reboot, I will receive the above message.  I've included the fstab and blkid info below.  

Any help would be appreciated.

fstab info.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/mail1-root /               ext4    errors=remount-ro 0       1
ro,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0 0     1
# /boot was on /dev/sda1 during installation
UUID=84d396ab-cbb0-4a9f-9021-433931e054fe /boot           ext2    defaults
  0       2
/dev/mapper/mail1-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




blkid info.

/dev/sda1: UUID="84d396ab-cbb0-4a9f-9021-433931e054fe" TYPE="ext2"
/dev/sda5: UUID="wXXXvd-PCYd-Btmi-dtm6-bAMN-PZxT-5Gwe2v" TYPE="LVM2_member"
/dev/mapper/mail1-root: UUID="4c879997-b9f3-4b36-8d1c-be7f7ebe038e" TYPE="ext4"
/dev/mapper/mail1-swap_1: UUID="c545b795-1024-4bea-9119-5ce9d6d149bf" TYPE="swap"


Thank you in advance.

---

