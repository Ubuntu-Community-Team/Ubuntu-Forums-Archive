---
title: "Screenshot -  Partition table querry?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-03
[http://i348.photobucket.com/albums/q339/BoyntonStu/8GBPartition-1.jpg](http://i348.photobucket.com/albums/q339/BoyntonStu/8GBPartition-1.jpg)

11.10 is installed on a PC with 2 GB of memory.

A few questions:

Are these partitions necessary?

What happens when/if the first partition becomes filled?

Does it make sense to use Gparted to enlarge the first partition to the entire 8 GB?

---

### Post by oldfred on 2012-05-03
Is this a full install on your flash drive?

I have a full install of 12.04 on a 16GB flash with 8GB for / and 8GB for data and no swap. I do have 4GB of RAM so I almost never use swap. But my install is just for testing, more on my laptop where I have little hard drive space.

I normally suggest 10GB as a minimum for /, but if using as a full system you may want larger if space is available.

---

### Post by Boyntonstu on 2012-05-03
> **oldfred said:**
> Is this a full install on your flash drive?

I have a full install of 12.04 on a 16GB flash with 8GB for / and 8GB for data and no swap. I do have 4GB of RAM so I almost never use swap. But my install is just for testing, more on my laptop where I have little hard drive space.

I normally suggest 10GB as a minimum for /, but if using as a full system you may want larger if space is available.

Thanks,

Yes, it is a full 11.10 install on the 16 GB flash drive.

My data will be saved on the PC 500 GB drive or on an external 400 GB drive.

Why not use 16 GB for /?

I think that 1 GB of swap is a waste.

If there was no data/free partition would the data be saved on /?

---

### Post by NikTh on 2012-05-03
if i remember correctly the  Ubuntu installer suggests at least 4.5Gb of space to install Ubuntu. Of course thats the limit. I agree for 10Gb for / and for /home , as more as you can. 
For Usb i prefer the LiveUsb (created with  "Ubuntu live usb creator"with a  [persistence]("http://en.wikipedia.org/wiki/Persistence_%28computer_science%29") space) . I think its much speeder and runs to all machines.

---

### Post by Boyntonstu on 2012-05-03
> **NikTh said:**
> if i remember correctly the  Ubuntu installer suggests at least 4.5Gb of space to install Ubuntu. Of course thats the limit. I agree for 10Gb for / and for /home , as more as you can. 
For Usb i prefer the LiveUsb (created with  "Ubuntu live usb creator"with a  [persistence]("http://en.wikipedia.org/wiki/Persistence_%28computer_science%29") space) . I think its much speeder and runs to all machines.

If there is zero swap space with Ubuntu use the PC RAM?

My concept is "Have Live USB Ubuntu, will Travel".

However, my first attempt in booting on another PC failed.

It started to boot and then began giving OK loads and halted.

Is there a check list of suggestions on what to do to make it boot on a new machine?

Does my screenshot show a /home directory?

---

### Post by NikTh on 2012-05-03
> **Boyntonstu said:**
> If there is zero swap space with Ubuntu use the PC RAM? 
Yes but i don't think ever needed. If pc has 2Gb of RAM , then swap memory is almost useless(depends of course on what programs you use.. lightweight of heavy) 

> **Boyntonstu said:**
> My concept is "Have Live USB Ubuntu, will Travel".
My concept too. I already made Liveusb and already loaded successfully up to 4 machines , just to show (to my friends) what they are missing.. :p

> **Boyntonstu said:**
> However, my first attempt in booting on another PC failed.
Maybe regular installation is responsible for this. i am not sure.

> **Boyntonstu said:**
> Is there a check list of suggestions on what to do to make it boot on a new machine? 
Just make a Liveusb with already included tool.. "start up disk creator" . Pull the "stored in reserved extra space" to the end so you can store data on that LiveUsb. 
I think it must be a Fat filesytem.. 

> **Boyntonstu said:**
> Does my screenshot show a /home directory?
I don't see /home partition , but root and free space. 

My suggestion is NOT a regular installation . Its just a LiveUsb with extra space to save your data , eg: firefox bookmarks , documents , even music...

---

### Post by oldfred on 2012-05-03
With a full install you may have to add boot options like the nomodeset to get it to work with other systems. You should not install any proprietary drivers if trying to boot different systems. Video & wireless are the most common issues.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

You need to post fstab or mount to see if /home is a separate partition, you should know as any auto installs do not create a separate partition for /home and you have to manually create it.

---

### Post by Boyntonstu on 2012-05-03
> **oldfred said:**
> With a full install you may have to add boot options like the nomodeset to get it to work with other systems. You should not install any proprietary drivers if trying to boot different systems. Video & wireless are the most common issues.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

You need to post fstab or mount to see if /home is a separate partition, you should know as any auto installs do not create a separate partition for /home and you have to manually create it.


Could not run fstab?

boyntonstu@boyntonstu-s5704y:~$ mount
/dev/sdb5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/boyntonstu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=boyntonstu)

This is the Home Directory

[http://i348.photobucket.com/albums/q339/BoyntonStu/Home.jpg](http://i348.photobucket.com/albums/q339/BoyntonStu/Home.jpg)

---

### Post by oldfred on 2012-05-03
So is /home on your hard drive? 

If so that is why it will not boot on other systems.

 sudo cat /etc/fstab

---

### Post by Boyntonstu on 2012-05-03
> **oldfred said:**
> So is /home on your hard drive? 

If so that is why it will not boot on other systems.

 sudo cat /etc/fstab


AFAIK, /home is on my computer which is the USB flash drive.

Above Computer are Devices:  the external DD, the hp SYSTEM, and the hp OS.


I am trying to understand where /home is generated.


boyntonstu@boyntonstu-s5704y:~$ sudo cat /etc/fstab
[sudo] password for boyntonstu: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=9c950be4-4d95-4e18-b41a-6c6e1fc5fb72 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b8e517ac-d381-4df1-ac46-e05e49d1afbc none            swap    sw              0       0
boyntonstu@boyntonstu-s5704y:~$

---

### Post by oldfred on 2012-05-03
You do not have a separate /home partition, it is just a folder in / (root) like all the other system folders. That is the normal default install of Ubuntu.

---

### Post by Boyntonstu on 2012-05-03
> **oldfred said:**
> You do not have a separate /home partition, it is just a folder in / (root) like all the other system folders. That is the normal default install of Ubuntu.

O.K  Thanks,

That clears up /home.

Is any other partition required in addition to / (root)?

---

### Post by oldfred on 2012-05-03
For servers (and old instructions you may find) often suggest to separate just about every system folder.

I think Herman only has /, and uses a swap file rather than a swap partition.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I have multiple systems installed so I separate my /home and the data stored in /home into data partitions. Then I can mount/use the same data in every install. Best not to share /home as the settings may conflict.

---

### Post by Boyntonstu on 2012-05-04
> **oldfred said:**
> For servers (and old instructions you may find) often suggest to separate just about every system folder.

I think Herman only has /, and uses a swap file rather than a swap partition.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I have multiple systems installed so I separate my /home and the data stored in /home into data partitions. Then I can mount/use the same data in every install. Best not to share /home as the settings may conflict.


If there is data in a partition i.e. Home,, and you change the partition to / (root) by expanding into it,  what happens to the data?

---

### Post by oldfred on 2012-05-04
Not quite understanding. You can copy data from /home to a data partition or vice-versa. Or if using partitioning tools you can shrink (within limits of data) or expand & the partitioning tool will keep the data.

This is to move /home to a separate partition
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Boyntonstu on 2012-05-04
> **oldfred said:**
> Not quite understanding. You can copy data from /home to a data partition or vice-versa. Or if using partitioning tools you can shrink (within limits of data) or expand & the partitioning tool will keep the data.

This is to move /home to a separate partition
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


Thanks,

I have a 16 GB USB flash with a complete 11.10 install that has half as its root partition.

I want to expand root to partition the entire 16 GB as /.

Is this possible without moving/copying data?

---

### Post by oldfred on 2012-05-04
If you have nothing else on the rest of the 16GB flash, all you have to do is expand the partition after moving or deleting swap. If the rest is still unallocated it has no data. If a partition then it may have data you have to backup first, then delete that partition. You cannot do this from the install on the USB as the partition has to be unmounted

If you still have the swap you have to move it first. If you delete swap and recreate it then you have to update fstab with the new UUID.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by Boyntonstu on 2012-05-04
> **oldfred said:**
> If you have nothing else on the rest of the 16GB flash, all you have to do is expand the partition after moving or deleting swap. If the rest is still unallocated it has no data. If a partition then it may have data you have to backup first, then delete that partition. You cannot do this from the install on the USB as the partition has to be unmounted

If you still have the swap you have to move it first. If you delete swap and recreate it then you have to update fstab with the new UUID.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)


Thanks,

Great and accurate advice (as usual).:)

---

