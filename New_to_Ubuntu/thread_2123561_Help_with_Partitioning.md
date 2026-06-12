---
title: "Help with Partitioning"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by RonM32 on 2013-03-08
Hello, I'm new to Ubuntu and I wanted to know how after Ubuntu is installed to make a new Partition that it uses for my music and what not. I have GParted open and the amount of space for the partition set aside, I just wanted to know like what file system to make it along with how after creating it selecting to use that Partition for my storage. I don't know I can do this or not since Ubuntu was originally installed on my main Drive, could I possible move it to this new Partition? Any help would be greatly appreciated.

Ron

---

### Post by vanadium on 2013-03-08
Not clear what you finally want to do. To create and use the extra space as a partition for data space, create the partition and format it with the ext4 file system. The make sure it is automatically mounted during startup. This can all be done graphically using disk utility, which is installed by default.

Moving your entire /home partition would be more complicated. There are several guides to do so (did it once myself), including this one: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

To move your entire Ubuntu installation to the new partition, by far the easiest approach is to reinstall: in less than an hour, you will have your system installed how and where you want it, almost fully automatically. During installation, you can, if you wish, install /home on a separate partition. The default installation installs it all in one partition.

---

### Post by ibjsb4 on 2013-03-08
If you want a partition just for storage you can install a "data partition".  If you need only linux access you can create an ext4 partition.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by RonM32 on 2013-03-08
Alright thanks, I got the partition set up which is all i really was concerned about, my only problem is when i try to put something on there it says i do not have permission to do it, how to i go about fixing that?

---

### Post by ibjsb4 on 2013-03-08
You need to give yourself write permission

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partition+write+permission&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partition+write+permission&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-03-08
Best to mount with fstab.
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If manually mounting:

 sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
sudo chown $USER:$USER /mnt/data
#if not known to list partitions
sudo fdisk -l

Be very careful with any chmod or chown with the -R option. That also changes all sub-folders. And if you modify permissions or ownership of any system partitions you just might as well reinstall. 
But changing data partitions it is the easiet way to update all files & folders.

---

