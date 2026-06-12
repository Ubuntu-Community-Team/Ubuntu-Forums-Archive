---
title: "Making directories and adding HDD"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by mayfield2 on 2013-08-01
Hi everyone just a little query, I have an Ubuntu server 12.04 installed and so far running pretty well, when making directories from a terminal using mkdir do I then need to mount a hdd to that directory? I'm a little confused as I come from a windows background. If I had say 3 HDD in this server and I need to create a directory for movies and I want these files to be on the 3rd HDD, am I right in thinking I create a directory and then mount the 3rd HDD to this movies directory?

---

### Post by The Cog on 2013-08-01
You are right. 
If you want to mount a new hard disk, you have to have a directory to mount it into. This directory would normally be empty (until you mount the hard disk there), and would normally be created especially for that purpose. For disks that are permanently mounted, the traditional place would be in /mnt, so you might create /mnt/movies and mount the disk there. /media is a more recent place for mounting disks, but by convention is for removable media. Note that directories come and go in /media, but this is done by scripts in the background that react to inserted media. They still go through the process of creating a directory and then mounting the disk to it.

---

### Post by mayfield2 on 2013-08-01
Thanks or the reply Cog, another question If I were to create additional folders for HDD3 say a music folder would I then mount this drive to that folder again

---

### Post by The Cog on 2013-08-01
You want to mount the same drive into two different folders? Yes, that's possible but I can't think why you would want to do it. Both folders would of course always have identical contents.

---

### Post by mayfield2 on 2013-08-01
OK I think I need to do more reading I'm trying to get my head around mounting HDDs as I've been googling how to's but don't really understand what and why you need to mount HDDs. I have mounted a hdd to a directory and other computers on the network can see it.

Thanks I'll be back with more questions you can be sure o that

---

### Post by oldfred on 2013-08-01
Some specific commands and links to more info:

This creates a mount and is how to set ownership & permissions:
 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

then you want to permanently mount with fstab.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

Then you may want to link folders in the data partition back into /home.

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

