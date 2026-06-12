---
title: "Can't access Hard drives"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Tommy The Cat on 2008-07-13
I've got two hard drives, hd0 and hd1. Upon trying to mount these hard drives, I get a an error that says that the locations could not be found. I've used the commands "sudo mount /dev/hda1","sudo mount /dev/hda1 /media/windows" (since hda1 is an ntfs drive), and I've also used "sudeo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222" (and I've tried putting hda1 in for sdb1).

What wierds me out even more is that I can't even mount or access the hard drive that Ubuntu is installed onto (hda0).

Most of these commands are from googling up "accessing hard drive ubuntu" or "mounting hard drive ubuntu", so, needless to say I'm a complete newbee. (Thus, I am here.) 

Also, from what I understand, the location /etc/fstab is pretty important. I can't find any fstab folders/files under etc. 

Help Please. *white flag*

---

### Post by bigken on 2008-07-13
[http://www.ntfs-3g.org]("http://www.ntfs-3g.org/")


just do search for ntfs in add remove programs

---

### Post by PmDematagoda on 2008-07-13
Are you using Ubuntu at the moment? If so, post the output of:-
```
cat /etc/mtab
```

---

### Post by Tommy The Cat on 2008-07-13
The command gives me 

/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sda1 /dos fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/you/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=you 0 0

---

### Post by PmDematagoda on 2008-07-13
Well, according to mtab, both drives are already mounted, sda1 at /dos and sdb1 at /.

---

### Post by Panos on 2008-07-13
> **PmDematagoda said:**
> Well, according to mtab, both drives are already mounted, sda1 at /dos and sdb1 at /.

Hi

I, and it seems others too, had a similar issue, pls see [http://ubuntuforums.org/showthread.php?t=850881](http://ubuntuforums.org/showthread.php?t=850881).

I think this is due to a new kernel, but I can't find anything related in kernel.org. IMHO, this is a major change and users should be notified somehow before upgrading the kernel.

Panos

---

