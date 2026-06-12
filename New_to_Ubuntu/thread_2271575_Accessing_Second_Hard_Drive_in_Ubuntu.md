---
title: "Accessing Second Hard Drive in Ubuntu"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by houmingc on 2015-03-31
When i run Disk Usage Analyzer, 3 component appear
1/ ste
2/ 9.4MB Volume
3/ Home Folder

item 2  could not scan folder.

When i lsblk
sda                         8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1                      8:1    0 298.1G  0 part /hdd
&#9492;&#9472;sda2                      8:2    0     9M  0 part /media/ste/ea853a1d-3d86-4e6
sdb                         8:16   0 119.2G  0 disk 
&#9500;&#9472;sdb1                      8:17   0   243M  0 part /boot
&#9500;&#9472;sdb2                      8:18   0     1K  0 part 
&#9492;&#9472;sdb5                      8:21   0   119G  0 part 
  &#9500;&#9472;ste--vg-root (dm-0)   252:0    0 115.1G  0 lvm  /
  &#9492;&#9472;ste--vg-swap_1 (dm-1) 252:1    0   3.9G  0 lvm  [SWAP]


When i df -Th
none                     tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                     devtmpfs  1.9G  4.0K  1.9G   1% /dev
tmpfs                    tmpfs     384M  1.3M  382M   1% /run
none                     tmpfs     5.0M     0  5.0M   0% /run/lock
none                     tmpfs     1.9G  156K  1.9G   1% /run/shm
none                     tmpfs     100M   40K  100M   1% /run/user
/dev/sdb1                ext2      236M   96M  129M  43% /boot
/dev/sda1                ext4      294G   63M  279G   1% /hdd
/dev/sda2                ext4      7.8M   84K  7.0M   2% /media/ste/ea853a1d-3d8


When GParted, it detects two drive
1/ /dev/sda (298.09Gib)
2/ /dev/sdb (119.24Gib)


When sudo lshw -C disk
 
  *-disk                  
       description: ATA Disk
       product: Hitachi HDS72103
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: JPFO
       serial: JPF421HA3HXG9V
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=9e399e39
  *-disk
       description: ATA Disk
       product: PLEXTOR PX-128M3
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 1.01
       serial: 002202105141
       size: 119GiB (128GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00041a3e
 




How can i get the second HDD mounted using fstab?

---

### Post by kerry_s on 2015-03-31
just go into disks-> mount options, just turn it on, no fstab editing needed.

---

### Post by oldfred on 2015-03-31
I do not use LVM nor know much about it, but everything is inside the LVM or logical partitions, not the physical partitions the LVM is using.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by houmingc on 2015-03-31
Under Disk Usage Analyzer or GParted, there is no disk tab.
Can be more precise?

Many Thanks.

---

### Post by oldfred on 2015-03-31
Depending on version it should look similar to these, shows tiny icon on upper right and then the menu you get. Click on Smart Data. It can run lots of tests, but all I know is passed or ok is good and just about anything else is a new drive.

---

### Post by kerry_s on 2015-03-31
> **houmingc said:**
> Under Disk Usage Analyzer or GParted, there is no disk tab.
Can be more precise?

Many Thanks.

just "disks" click on your drive you want mounted, on the bottom left click on the gears

(sorry about that, running dual screens)

---

### Post by houmingc on 2015-03-31
I learn a new ubuntu app call Disks. :> Thanks
When reboot, i notice "An error occurred while mounting /media/SecondDrive"
sudo nano /etc/fstab, attempt to erase what i wrote. Now Working.

Currently, i can't dump files into GUI /media/SecondDrive
Attempt to change mount point Owner using chown

==1st attempt==
Under Mount Option, i select "show in user interface", but not working.

==2rd attempt==
ste@ste:/media$ ls -l
total 12
drwxr-xr-x  2 root root 4096 Feb  1 11:31 home
drwxr-xr-x  4 root root 4096 Apr  1 09:55 SecondDrive
drwxr-x---+ 2 root root 4096 Apr  1 05:40 ste

 sudo chown ste:ste /media/SecondDrive  -> now files can be dump into GUI :>

Now i want to create a shortcut folder in my desktop symbolically linked to /media/SecondDrive. How to do it ?

---

### Post by kerry_s on 2015-03-31
> **houmingc said:**
> I learn a new ubuntu app call Disks. :> Thanks
Currently, i can't create a folder in GUI /media/SecondDrive
How to change the mount point with chown

Under Mount Option, i select "show in user interface", but not working.

all you have to do is turn it on & reboot, don't change nothing else.

---

### Post by oldfred on 2015-03-31
I put folders into my shared data partition. I use /mnt/data but it can be anything you like.
And then I link each folder back into /home. I normally do this before doing anything that might add data to default folders, so I just delete the defaults and use links. If you have data in your folders be sure to back that up before  linking a folder with the same name.

Splitting home directory discussion and details:
See post #4
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

