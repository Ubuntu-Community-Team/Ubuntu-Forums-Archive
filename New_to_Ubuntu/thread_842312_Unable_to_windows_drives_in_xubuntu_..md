---
title: "Unable to windows drives in xubuntu ."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by higatech on 2008-06-27
hi ,
Plz tell me how can i see windows drive in xubuntu ....

---

### Post by sharks on 2008-06-27
So the way I figure it, if you want to mount your windows partition on Xubuntu, which is the flavour of Ubuntu I use, you got to edit the fstab fil in /etc

So since your editing a kickass system file what you should do is back it up.

> 
sudo cp /etc/fstab /etc/fstab_backup
sudo vi /etc/fstab


Make the directory where you want your drive mounted, I chose /mnt/windows

> sudo mkdir /mnt/windows

The syntax for the fstab files is:

file system mount point type options dump pass

So you append the following lines to your file:


file system mount point type options dump pass
> /dev/hda1 /mnt/windows ntfs'+' noatime,defaults,users,ro,umask=0 0 0

NOTE: My code div isn't handling the width overflow properly. There's a couple of tabs after ntfs, and the '+' indicates the same line, not a new line.

hda1 is mostly your C drive. If your drive is FAT32 you change the ntfs to vfat.

if you don't feel like mounting it at boot time then just make the directory and run this at a terminal


> sudo mount /dev/hda1 /mnt/windows ntfs'+' noatime,defaults,users,ro,umask=0 0 0

NOTE: My code div isn't handling the width overflow properly. There's a couple of spaces after ntfs, and the '+' indicates the same line, not a new line.

and to unmount


> sudo umount /mnt/windows

---

### Post by drs305 on 2008-06-27
To easily mount and use NTFS drives and add the entry to your fstab, there is an app called ntfs-config.

Install it with:
```
sudo aptitude install ntfs-config
```

To start it:
```
sudo ntfs-config
```
or:
System Tools, NTFS Configuration Tool

---

