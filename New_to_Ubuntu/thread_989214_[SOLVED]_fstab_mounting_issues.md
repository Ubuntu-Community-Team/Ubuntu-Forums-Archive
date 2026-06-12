---
title: "[SOLVED] fstab mounting issues"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-21
I have a hardware RAID1 showing in fdisk -l as /dev/sda1. This is not the drive that Kubuntu is on, thats located on /dev/sdb1. I don't know how they became backwards, but it works... I attempted to "mount /dev/sda1 /mnt/Mirror" and I can see it but can't write to it. Ideally, I wanted this mounted by fstab so I started reading bodhi.zazen's guide on it. I added:
```
# /dev/sda1
LABEL=Mirror 	/mnt/Mirror	ext3 	default 	0	0
```
to /etc/fstab and it mounted but again my user could not edit files. I changed "default" to "users,noauto,rw" and when KDE4 loaded received an error stating: > An error occurred while accessing 'Mirror', the system responded: org.freedesktop.Hal.Device.Volume.PermissionDenied: Device /dev/sda1 is listed in /etc/fstab. Refusing to mount.
I then changed "users.noauto,rw" back to "defaults" and can not write. What am I doing wrong?

---

### Post by taurus on 2008-11-21
I believe there is a s after the default.

```
# /dev/sda1
LABEL=Mirror 	/mnt/Mirror	ext3 	default**[COLOR="Blue"]s[/COLOR]** 	0	0
```

And if you want to be able to write to /mnt/Mirror, you can change the ownership of that directory from root to your login name.  Assuming your login name is scribbles, you could do something like

```
sudo chown -R scribble:scribbles /mnt/Mirror
ls -la /mnt/Mirror
```

---

### Post by scribbles on 2008-11-21
Solved!

---

