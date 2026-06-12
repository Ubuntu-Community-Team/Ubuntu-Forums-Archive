---
title: "Ubuntu 16.10 Ext4 internal hard drive no write/read permissions"
date: 2016-11-17
forum: New to Ubuntu
---

### Post by x10234 on 2016-11-17
So, since I have installed Ubuntu I have had no read/write permissions on one of my hard drives. From what I found online is that when you do  ''ll /media/josiah'' I'd find my hard drive and it would say that it was under root command and in my case it isn't. (colored is from terminal). I need help figuring out how to give myself read and write permission as a normal user. I already know how to find the UUID so you do not have to provide that info. 

[COLOR=#800000] ll /media/josiah
total 12
drwxr-x---+ 3 root root 4096 Nov 16 08:56 ./
drwxr-xr-x  3 root root 4096 Nov 16 00:55 ../
drwx------  3  999  999 4096 Nov 17 05:18 Disky McDiskface/
[/COLOR]
The hard drive I am wanting permissions to is 'Disky McDiskface'.

Hopefully you guys can help me here! :)

---

### Post by oldfred on 2016-11-17
When labeling partitions I prefer to not use spaces. I use CamelCase, under_score, or justonename.

I label all partitions, but only mount some in fstab that I want all the time.
And then the mount point I create does not have to be label. I have confused myself by labeling a partition Data, but mounting at /mnt/data. In Linux case is important so Data is not equal to data.

If internal drive & partition, you need to create mount point (best if no spaces), edit fstab with UUID, mount, format and details as per examples in link.
And then you need to give  yourself ownership & permissions.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. NTFS & ext4 examples
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If not automounted to some mount point you can set ownership & permissions.
If already mounted change /mnt/data to your mount.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

