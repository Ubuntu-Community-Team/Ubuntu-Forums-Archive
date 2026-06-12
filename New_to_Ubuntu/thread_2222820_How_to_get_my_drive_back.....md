---
title: "How to get my drive back...."
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Pierre Dartigues on 2014-05-08
My drive /dev/sda6  is unreachable to me. I made the partition for myself to put data on but somehow only root has rights there. How can I get it (and its containt)  back to my personal account?
I am an absolute dummy but I managed nevertheless to rebuild the GRUB after changing partition sizes, so I can manage to use the konsole, if it is not too difficult......[IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG]
Greetz, Pierre

---

### Post by kc1di on 2014-05-08
Hi Pierre Dartigues and welcome to Ubuntu,

You need to use the change owner command [here's a page]("http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user") that will tell you how to do that.

and[ here's another page]("http://itsfoss.com/set-write-permission-ext4-partition-ubuntu-linux/") with more detailed instructions.

good luck ;)

---

### Post by Pierre Dartigues on 2014-05-08
Thanks a lot David, I seem to be saved for now..... I think I managed all right..... I am the owner of the disk and I can create, modify and delete files. I wonder if the some 3 Gb that is in use may be made visible to me, or does it belong to Ubuntu? It seems so much to me......

---

### Post by Pierre Dartigues on 2014-05-08
Btw, the disk that I lost end now made my own (1ffc3999-8c05-4c99-a487-1c96c4888037) now is not in this list:


pieter@Saturnin-00:~$ ll /media/pieter
totaal 36
drwxr-x---+  6 root   root    4096 mei  8 13:23 ./
drwxr-xr-x   5 root   root    4096 apr  1 20:32 ../
drwx------  12 pieter pieter 16384 jan  1  1970 CA9F-AA40/
drwxr-xr-x  23 root   root    4096 mei  8 08:44 da8c991c-c72b-4efd-899d-a2531d018c97/
drwx------   1 pieter pieter  4096 mrt 13 23:10 Data-03/
drwxr-xr-x   4 root   root    4096 apr  1 19:43 Suse 13.1/

Should that be repaired?

---

### Post by oldfred on 2014-05-08
Ubuntu reserves 5%, on a data drive you can reduce that as long as you know whether it is getting full or not. 
       Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3


did you mount partition with fstab somewhere else? I usually mount data partitions in /mnt/data and link folders into my /home. But then I cannot see data partition, which I do not want to to avoid confusion as I have the folders already.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

I do this to give myself ownership & permissions. If already mounted you do not have to remount as you can only mount once.

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

### Post by Pierre Dartigues on 2014-05-09
Thanks a lot for your explanation, Oldfred.

---

