---
title: "Fdisk for partitioning"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by kkb33 on 2008-08-02
I have windows vista and ubuntu installed on my computer.  I know vista is on dev/sda1 and dev/sda2 but I have extra ubuntu installed that I don't need.  I want to keep the ubuntu I am using but delete the other partitions but I'm not positive of which partitions to delete.  this is what fdisk and then p outputs:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8684380

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97659103+   7  HPFS/NTFS
/dev/sda2           17930       19457    12266496    7  HPFS/NTFS
/dev/sda3           12159       15648    28033425   83  Linux
/dev/sda4           15649       17929    18322132+   5  Extended
/dev/sda5           17689       17929     1935801   82  Linux swap / Solaris
/dev/sda6   *       15649       17597    15655279+  83  Linux
/dev/sda7           17598       17688      730926   82  Linux swap / Solaris

and when I do mount it says this:
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

I am assuming I am using sda6 but would the other one I want to keep be sda3 since the id for both of them is 83? I really don't know what I am doing and am worried I will mess up my computer! Thanks for any suggestions!

---

### Post by Pro-reason on 2008-08-03
Never mind the "ID" part.  Pay attention to the device identifier (/dev/...), and the filesystem type.

You can also enter "sudo blkid" for more info about your drives.

Also try "gksu gparted".

---

