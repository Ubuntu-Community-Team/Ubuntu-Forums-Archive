---
title: "Mounting permissions"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by patty&amp;selma on 2013-06-09
Hi

I've got a ext2 (or ext3) HDD connected to my linux TV reciever, and now I want to connect and write to it with my PC. Mounting it isn't a problem, but I don't have writing permissions. I've tried mounting it on a Mac with various software, on Windows with various software, and on Linux Mint with a mount point - all to no avail. Could anyone steer me in the right direction please?

I've used swap files on the HDD with the receiver - not sure if that makes any difference. 

Thanks

On another note - if I were to reformat the disk (which I really don't want to do) on my current linux distro, would I always have writing permissions thereafter, or could I lose them again?

---

### Post by oldfred on 2013-06-10
If you want to permanently mount with fstab.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

You may need to set ownership & permissions:

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

---

