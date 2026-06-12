---
title: "cannot mount hard drive."
date: 2008-07-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-17
trying to mount external hard drive under fat 32 format to transfer some files to my girlfriend's windows pc. cannot mount even via terminal help

---

### Post by iaculallad on 2008-07-17
> **PatrickMoore said:**
> trying to mount external hard drive under fat 32 format to transfer some files to my girlfriend's windows pc. cannot mount even via terminal help

```
sudo mkdir /media/fat32
sudo mount -t vfat /dev/hdaX /media/fat32
```

where:

hdaX = FAT32 partition, you could view this by listing your drive using fdisk.

```
sudo fdisk -l
```

---

### Post by kunixos on 2008-07-17
if that doesn't work
```
sudo mount -f -t vfat /dev/hdaX /media/fat32
```
the '-f' option forces it to mount. this is a problem when windows 'improperly' removes an external drive. sometimes you have to force mount.

Hope this helps!

---

### Post by PatrickMoore on 2008-07-17
how do i set the permission to write to it thank you for helping me mount it

---

### Post by iaculallad on 2008-07-17
> **PatrickMoore said:**
> how do i set the permission to write to it thank you for helping me mount it

You can't write to the mounted drive?

What about placing the configuration on your fstab file:

Unmount it first:

```
sudo umount /dev/hdaX
```

and open fstab file for editing:

```
gksudo gedit /etc/fstab
```

and add the line of text below on the last line of the file:

> /dev/hdaX /media/fat32 vfat defaults,umask=000 0 0

Save and Close the file. Then, try mounting it:

```
sudo mount -a
```

---

### Post by PatrickMoore on 2008-07-17
i forgot how to change permission so that i can write to the hard drive anyone know how

---

### Post by PatrickMoore on 2008-07-17
> **iaculallad said:**
> You can't write to the mounted drive?

What about placing the configuration on your fstab file:

Unmount it first:

```
sudo umount /dev/hdaX
```

and open fstab file for editing:

```
gksudo gedit /etc/fstab
```

and add the line of text below on the last line of the file:



Save and Close the file. Then, try mounting it:

```
sudo mount -a
```

i know that there is a less complicated way to do that  but im going to try that thanks

---

### Post by bodhi.zazen on 2008-07-17
You set permissions on FAT and NTFS at the time of mounting or in fstab.

I suggest the following options.

uid=1000,gid=100,dmask=027,fmask=137

dmask and fmask are similar to umask, d = directories and f = files.

The "problem" with umask=000 it then everything is executable and world readable.

---

