---
title: "unable to mount volume..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by nycjeff on 2008-04-27
I'm having trouble with any removable devices since I upgraded to Hardy.
When I tried to use my ipod it told me it was unable to mount volume 'JEFF'S IPOD'  I tried a usb memory stick and another mp3 player and none worked.
These things have worked before the upgrade.
Also, they seem to work when I add a user and plug them in under that user.

Any other information that I should look at to fix this problem?

FSTAB and MTAB below

FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=272b9a34-1cca-49be-8d61-9e8eef46abdb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e815c1ec-d94c-4aef-937a-eaef7d12a86b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc2 /media/JEFF'S\040IPOD vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1001,user,defaults,noatime,iocharset=utf8 0 0

MTAB:
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/jeff2/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jeff2 0 0

---

### Post by Peter09 on 2008-04-27
Go into system->administration->groups.

You can find out which groups you belong to. Check that you belong to at least the same groups as the users which can mount the drives. If you are an admin user do not come out of that group.

PC

---

### Post by nycjeff on 2008-04-27
yeah, I was in the same groups.

---

