---
title: "Disk Managerment"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by subrahmanyam on 2015-07-23
Hi,
I have completely removed windows and switched to Ubuntu 14.04 for which I am happy
But the entire 1 TB storage is in once device.
I want make paritions like those in windows(C,D,E..) to organize my data
Please help me out to do so

Thanks in advance

---

### Post by howefield on 2015-07-23
Use a Live DVD/USB to run the application gparted.

You can't use gparted on mounted partitions/disks hence the need to use a Live medium, but be careful :)

---

### Post by subrahmanyam on 2015-07-24
Thank you howefield,shall try that...

---

### Post by Mark Phelps on 2015-07-24
> I want make paritions like those in windows(C,D,E..) to organize my data

Strictly speaking -- you can't -- make partitions like those in Windows.  Why? Because the use of drive letters is unique to Windows; Linux does not use them.

Furthermore, Windows tends to concentrate system files on their "C:" drive, but once again, Linux does not use this convention.  In Linux, you have one big filesystem which is spread across partitions.  While you could create a separate partitition for storing data files, it is not a simple matter to do the same for apps because their pieces get installed across a variety of directories.

---

### Post by oldfred on 2015-07-24
I prefer smaller system partitions and larger data partitions. I use /mnt/data for most of my data and have folders for each of the standard folders in /home like Documents, Music, Videos etc.

You can create multiple data partitions, but a bit more difficult. One advantage of Ubuntu is that you do not use default names like d:, but do have to create a name or mount point like /mnt/data. 

Create partition(s) with gparted. Create mount points. Better to use ext4 if not dual booting with Windows, but you then also have to give yourself ownership & permissions to use it. 

       sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

If on internal drive better to use fstab and permanently mount it. You use a mount point like created above.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

Then you can link folders in your data partition into /home.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

