---
title: "[SOLVED] NTFS Partition"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by nebu on 2008-10-27
i use ubuntu 8.04

i have two NTFS partitions..... some of my files like my wallpapers etc are stored in the ntfs partitions....

when i start ubuntu.... for some reason the ntfs partitions arent automatically mounted.....

so my wallpaper never comes on....

only once i manually open the partitions through nautilus.... the wallpaper comes.....

how do i resolve this??

---

### Post by GumboLinux on 2008-10-27
I believe you use fdisk to convert it to like an ext2 or fat32 format which is more friendly with linux

---

### Post by jerome1232 on 2008-10-27
You'll need to create an fstab entry so that it will be mounted at boot time.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Feel free to ask questions about that link.

Basically what you'll do is run fdisk to list out your partitions, determine the device name then add an fstab entry

```
sudo fdisk -l
gksu gedit /etc/fstab
```

this is an example fstab entry, you would change /dev/sdxx to whatever your devices name is, and change the mount point. maybe the permissions to something more your liking. This one makes the drive readable/writable by everyone.

```
/dev/sda4 /media/ntfsdrive ntfs-3g umask=000 0 0
```

edit: you can also use a utility called ntfs-config I've heard it can make an fstab entry for you I haven't used it so I couldn't help you with that.

---

### Post by GumboLinux on 2008-10-27
yay at least I was correct bout fdisk :P

---

### Post by reg4c on 2008-10-27
You can also install the NTFS Configuration Tool

I used that so that I don't muck around with fstab by myself

Check all the disks and enable writing to external and internal drives

Works for me
Cheers

---

### Post by nebu on 2008-10-28
thx

tht worked

---

