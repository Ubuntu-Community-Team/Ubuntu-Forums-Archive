---
title: "Partition problems... Maybe"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by Wray on 2013-07-20
[COLOR=#0000ff]below is a print out of parted -l  I have a 1 TB drive but i cannot find a space larger than 13 GB for storing my photos ...and it is in /root!
I assume that also contains boot?   I have no idea how this state of affairs came about.
Do i have to mount the other logical extensions?  If so How?
As usual any help is greatly appreciated[/COLOR]






[SIZE=+1]Model: ATA WDC WD10EADS-22M (scsi)
      Disk /dev/sda: 1000GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos
      
      Number  Start   End     Size    Type      File system     Flags
       1      1049kB  20.0GB  20.0GB  primary   ext4            boot
       2      20.0GB  751GB   731GB   extended
       5      20.0GB  40.0GB  20.0GB  logical   ext4
       6      40.0GB  41.0GB  999MB   logical   ext4
       7      41.0GB  741GB   700GB   logical   ext4
       8      741GB   751GB   9999MB  logical   linux-swap(v1)
      
      
      Model: SanDisk Cruzer Fit (scsi)
      Disk /dev/sdh: 32.0GB
      Sector size (logical/physical): 512B/512B
      Partition Table: msdos
      
      Number  Start   End     Size    Type     File system  Flags
       1      16.4kB  32.0GB  32.0GB  primary  fat32        lba[/SIZE]

---

### Post by deadflowr on 2013-07-20
Try something like
```
df -h
```
As parted only shows the partition layout and not disk usages.

Mind you that df only shows mount partitions.

It seems you have five linux partitions on your system(ext4).
One primary, and four logical.
And they range in size from 20Gb to 700GB.

But it's unclear what each one is. 
And what the disk usage is.
Parted is only showing us the total capacity of the partition, but not the total in use/used.
Nor is it telling us which is a root partition and which is not.

---

### Post by Wray on 2013-07-20
> **deadflowr said:**
> Try something like
```
df -h
```
As parted only shows the partition layout and not disk usages.

Mind you that df only shows mount partitions.

It seems you have five linux partitions on your system(ext4).
One primary, and four logical.
And they range in size from 20Gb to 700GB.

But it's unclear what each one is. 
And what the disk usage is.
Parted is only showing us the total capacity of the partition, but not the total in use/used.
Nor is it telling us which is a root partition and which is not.


[COLOR=#0000ff]Thanks Dead. See results of df -h below  Am i going to be able to makes sense of this mess
 and fix it, or am i better off to just repartition/reformat the disk?


Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G  5.3G   13G  31% /
udev            3.0G  4.0K  3.0G   1% /dev
tmpfs           1.2G  900K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.0G  156K  3.0G   1% /run/shm
/dev/sda5        19G  173M   18G   1% /tmp
/dev/sda6       938M   84M  808M  10% /boot
/dev/sda7       642G  2.8G  607G   1% /usr
/dev/sdg1        30G  152M   30G   1% /media/16C8-0197[/COLOR]

---

### Post by oldfred on 2013-07-20
I have never made /usr a separate partition on a desktop. Some with servers or SSD may make it separate but that is huge.
 Explanation of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

I have 25GB / (root) partition including /home but all data in other partitions. And I use about 9GB. No other system partitions are anywhere except in /.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by Impavidus on 2013-07-20
You can move all data on your sda7 (the /usr directory) to sda1, move all data from /home to sda7 and change the mount point of /dev/sda7 from /usr to /home. This will give you 600GB of space in /home, which is the proper location to store photos. (/root should only be used for administartive purposes)

I'll try to find the exact commands you need.

---

### Post by Wray on 2013-07-20
> **Impavidus said:**
> You can move all data on your sda7 (the /usr directory) to sda1, move all data from /home to sda7 and change the mount point of /dev/sda7 from /usr to /home. This will give you 600GB of space in /home, which is the proper location to store photos. (/root should only be used for administartive purposes)

I'll try to find the exact commands you need.

[COLOR=#0000cd]If you can do that you will be my hero forever!

PS:  Can i recover the 232 GB unallocated also?
[/COLOR]

---

### Post by oldfred on 2013-07-20
I can quickly partitially help as this is the standard way to move a /home. Moving other system partitions would be similiar, but you have to copy first and edit fstab as you go.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Impavidus on 2013-07-20
The procedure will move most commands temporarily to a different directory, so it may not work while you are logged in as a normal user in a GUI. It will work from recovery mode. Reboot your computer, hit shift a few times to get the grub menu (if you don't get it automatically) and select recovery mode. When you get to a menu, select **Drop to root shell prompt**. You are now logged in as root with a minimum of software running.

Remount the root file system as read-write```

mount -o rw,remount /

```
Next make a temporary mountpoint for your /dev/sda7 and mount it```

mkdir /media/temp
mount /dev/sda7 /media/temp
```
You can use any name you want, as long as the directory doesn't exist yet.
At this point most commands in your system will have moved out of your PATH so you cannot access them by simply typing them, but you need to prefix them with /media/temp/bin/. This has freed your /usr directory, to which you can copy all contents of your old /dev/sda7. This will take some time.```

/media/temp/bin/rsync -aXS /media/temp/. /usr/.
```
Now you have moved your /usr. For the moment you can keep everything on sda7 too as a backup.```

mkdir /media/temp/old_usr
mv /media/temp/* /media/temp/old_usr
```
This may complain that it can't move old_usr to a subdir of itself. Don't worry. Next you can move your /home```

rsync -aXS --exclude='/*/.gvfs' /home/. /media/temp/.
```
This may again take some time.

Afterwards you can change fstab to change the mountpoint of sda7. Create a backup of /etc/fstab and open it for editing```

cp /etc/fstab /etc/fstab.old
nano /etc/fstab
```
**nano** is a text editor that can run in a command line interface. Find the line with **/usr** in the second column (ignoring any lines starting with #) and replace **/usr** with **/home**. Save the file (ctrl-x). Move the old /home directory to keep it as a backup for the time being```

mv /home /home_old
mkdir /home
```
When you reboot and log in as ordinary user it should work```
reboot
``` If everything is OK you can delete the backups of /usr and /home```

sudo rm -rf /home_old
sudo rm -rf /home/usr_old
sudo rmdir /media/temp
```
Does anyone see any details I missed?

---

