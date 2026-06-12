---
title: "mounting a USB flash drive that has ext4 formatting"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by cyclingchap on 2013-11-24
Hi,

I just used gparted to format a 32Gb USB flash drive to ext4 file system. This is because I want to run rsync between a folder on my ext4 ubuntu drive to the flash drive. I was getting write permission errors when using a FAT32 file system on the USB drive.

I successfully created the ext4 format of the flash drive, and change the label name.

Problem is now I can't read or write to it after mounting it.

I insert it in the USB port, it automatically mounts to /media/sandisk01  (sandisk01 is the label name I chose).

When I right click on the drive in the 'file manager' and look at properties it says that I am not the owner of the mounted drive and that I can't change permissions.

I've been running around the internet trying to find out how to change the permissions on this mounted ext4 drive to no avail.

Thanks

---

### Post by oldfred on 2013-11-24
I would update ownership & permissions. (# is comments)

       sudo chmod -R a+rwX,o-w /media/sandisk01
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.

sudo chown -R $USER:$USER /media/sandisk01

      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by cyclingchap on 2013-11-24
Hey, thanks. That worked.

I did try sudo chmod before and it didn't work. I was probably choosing the wrong options or something. I forgot about the chown command!

---

### Post by oldfred on 2013-11-24
Glad that worked.

You can change to solved.

---

