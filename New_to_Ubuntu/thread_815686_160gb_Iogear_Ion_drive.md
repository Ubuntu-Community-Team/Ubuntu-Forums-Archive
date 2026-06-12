---
title: "160gb Iogear Ion drive"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by g45model21 on 2008-06-01
I can even mount the ion drive on in terminal.

NTFS file system

after "sudo fdisk -l" I get:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x513a5139

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

and after "mount" I get:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

---

### Post by didac on 2008-06-02
It's not being recognized. Post:

```
dmesg | tail
```

---

