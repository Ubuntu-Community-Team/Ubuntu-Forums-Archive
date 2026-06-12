---
title: "Mount point root privileges"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by spud.dups on 2008-06-30
After installing Hardy, I was able to mount and unmount /dev/sda1 and /dev/sda2 (which are my windowsXP and my archive partitions, both NTFS) fine.  Wanting to learn more I decided to start playing with the mount and umount commands in terminal.  Problem is that now I can only mount /dev/sda1 as root.  I would like to know how to revert any changes back to how it was when I first installed Ubuntu.

If I remember correctly, the first command that gave me the problems was:

sudo /dev/sda1 /media/spud

and now it needs root privileges to be mounted.  Below is some output that may be helpful.

spud@baby-spud:/media$ mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
spud@baby-spud:/media$ mount /dev/sda1
mount: only root can mount /dev/sda1 on /media/spud

If you need any more information please let me know.  Thank you.

---

### Post by novatotal on 2008-06-30
as root
sudo /dev/sda1 /media
try that

---

### Post by Rocket2DMn on 2008-06-30
Can you please post
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

---

### Post by drs305 on 2008-06-30
For automounting, you can install and use ntfs-config. 

If you want ntfs-config to automatically handle the configuration, comment out the current NTFS entries in fstab. 

Install and run ntfs-config.
```

sudo aptitude install ntfs-config
sudo ntfs-config

```

It will ask to you select the nfts partitions to put into fstab.
Next it will ask for a new /media mountpoint (in the block, type just the name - example: myntfs )
Tell it you want write access and exit.

The auto fstab entry will look something like:
UUID=XXXXXX ntfs-3g  defaults,locale=en_US.UTF-8 0 0 

```
sudo umount -a
sudo mount -a
```

If you inspect the mount point, it will show root ownership but you will be able to read/write to all the files/folders.

---

### Post by spud.dups on 2008-07-01
It's probably not recommended, but I just went into the fstab and commented out the line that was in there set to auto mount.  Thanks for the help you guys.

---

