---
title: "get write permissions for Fat32 ext hd"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by mowbagz on 2012-08-29
I want to format my 500gb ext hd to have full permissions on mac and ubuntu. I want to use it on mac/linux/windows so I wonder what is the best way to do it.
It's FAT32 now and when mounting on linux I only get read-only permissions. 
I'm new to this and would appreciate your help!

---

### Post by ajgreeny on 2012-08-29
How are you mounting it in your linux OS?  Normally when you plug in a fat32 USB disk it is automounted with read/write permissions, so you must be doing something different.

---

### Post by irv on 2012-08-29
> **mowbagz said:**
> I want to format my 500gb ext hd to have full permissions on mac and ubuntu. I want to use it on mac/linux/windows so I wonder what is the best way to do it.
It's FAT32 now and when mounting on linux I only get read-only permissions. 
I'm new to this and would appreciate your help!

I would use gparted to format. If you dont have it installed just do this in a terminal
```
sudo apt-get install gparted
```
Now make sure that your 500 gig HD is connected to your computer (if it is external drive) If it is internal it should be already connected.
Run gparted and make sure you select the right drive. You don't want to format the wrong drive. If it is mounded you will have to unmount it to format it. Format it with fat32 and you should see it an all your systems. And after it is formated it should auto mount.
I know you can do all the formating at the terminal but if you are new to Ubuntu and want to see what is going on in the GUI then gparted is a good tool.

---

### Post by mowbagz on 2012-08-29
> **ajgreeny said:**
> How are you mounting it in your linux OS?  Normally when you plug in a fat32 USB disk it is automounted with read/write permissions, so you must be doing something different.

I'm only plugging it in and it mounts automatically. I can read files but not write on it.

---

### Post by irv on 2012-08-29
> **mowbagz said:**
> I'm only plugging it in and it mounts automatically. I can read files but not write on it.

open a terminal and type.
```
cd /media
```
then
```
ls
```
It should give you a list of mounted media. find your 500 gig HD and type
```
cd /(your Hd)
```
Then type
```
ls -l
```
Then copy and past your read out here. We can see who owns the files and what right are on the files.

---

### Post by oldfred on 2012-08-29
But if it is FAT32 then there are no ownership & permissions to change. Everything will be root but you can still read & write based on how mounted.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

I do not know how Nautilus mounts, I also thought it mounted read/write by default.

---

### Post by irv on 2012-08-29
> **oldfred said:**
> But if it is FAT32 then there are no ownership & permissions to change. Everything will be root but you can still read & write based on how mounted.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

I do not know how Nautilus mounts, I also thought it mounted read/write by default.

I agree it should. Opening my 32 gig SD card in Nautilus (which is a fat32) and looking at the properties it shows read and write permission. 
[ATTACH]223360[/ATTACH]

---

### Post by ajgreeny on 2012-08-29
Can we see your /etc/fstab file, just in case something has been added for the disk's mountpoint, and also the output of ```
ls /media
``` with the disk both attached and unattached.

---

### Post by c_cinq on 2012-08-29
it could be a case of not unmounting the hdd cleanly, try this [http://ubuntuforums.org/showpost.php?p=9762213&postcount=4]("http://ubuntuforums.org/showpost.php?p=9762213&postcount=4")

gparted > unmount > check

---

