---
title: "Howto: Create RAID5 and Expand/Grow it using mdadm without loosing data."
date: 2007-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by PumpAction on 2007-08-04
I write this guide because i found a lot of info on the subject but still i had some problems because a lot of the info was very out-of-context it dealt with very specific problems and no clue if I had/should do anything before or after. With this guide I try to cover the whole process, thats why I've included a plan over what I have to to before I actually comes with the specific commands to type in terminal. This guide got some bloat that you might not need, to skip it; search this page for "blabla" and take it from there. For more information about what those commands are suppose to do read the bloat:

I make this guide while experimenting to get the process right for creating and expanding a raid 5 array.
My situation is: I got three 320gb sata disks which is empty, and another three which is full, I want to combine all six sata disks in one raid 5 array.
I got no way to back it all up and format all disk and set up a 6 disk raid-5 from scratch, so if my idea was to set up a raid5 with 3 disks move over some data and, format the now empty disk and expand the array to cover the new disk. Then repeat the process until its all six disks in one array. This is of course not critical data that, that why I don't got backups. Loosing it is only inconvenient, I am aware of this SO SHOULD YOU BE IF YOU FOLLOW THIS GUIDE. IF DATA ARE IMPORTANT HAVE BACKUPS AND DONT BLAME ME IF YOU LOOSE DATA. I'm no Ubuntu/Linux/RAID expert, this guide is more of a collection of other guides aimed at solving one specific set of problems. I write this guide while testing everything i do on six small partitions spread over the three empty disks, it is my advise that you to "try-it-before-you-buy-it".

In advance I have made some preparations which i won't cover in this guide. This is:
Prepare some files with a checksum (sfv). which i use as a quick check to see if my files are ok after expansion.
I also know my partitions very well, almost to the point that i could point them out on the platters :P
Also my system is up and running with a working internet connection and has access to apt-get

This howto will try to cover the whole process of setting up a raid5 array and expanding/growing it on a system already up and running. This guide will NOT show you how to use a softraid5 array as basis for your operating system or anything like that. This simply shows you how to take a bunch of disks turn them into a raid5 and how to expand it later without loosing data.

[B]
[repeatmyself][/B]
I write this guide because i found a lot of info on the subject but still i had some problems because a lot of the info was very out-of-context it dealt with very specific problems and no clue if I had/should do anything before or after. With this guide I try to cover the whole process, thats why I've included a plan over what I have to to before I actually comes with the specific commands to type in terminal.
**[/repeatmyself]**

**What I've got:**
Three full 320gb harddisk
Three empty 320gb harddisk
Ubuntu Feisty Fawn (7.04) 32-bit installed on some other completely separate disk.
Access to gparted, cksfv, mdadm either already installed or via apt-get install and a working internet connection

**The todo list human mode:**
Create raid5 with 3 empty disks/partitions
Copy data to raid5 array
Expand raid5 array and its filesystem with one (or more) disk/partition

*This simple plan is a bit more complicated for the computer. Here is it's version:*

**The todo list computer mode:**
**----Make softraid section----**
Prepare partitions to be used in array and set raid flag, format and set raid flag
Create raid array with mdadm
Format (make filesystem) raid array
Mount the brand new and flashingly good looking supercool new ready to be used raid 5 array
Copy files

**----Expand section----**
Unmount the brand new and flashingly good looking supercool new ready to be used raid 5 array
Prepare and the new partition to be added
Put the new partition under softraiddriver control
Tell driver to grow on to the new disk
Check filesystem integrity
Expand filesystem so you get more space to play with
mount the expanded array
Check the integrety of your files

[SIZE="3"]**The terminal commands, no more blabla:**[/SIZE]
This is where it get serious, these are the commands I've used. MAKE SURE YOU CHANGE EVERYTHING THAT NEEDS TO BE CHANGED like device names and path, number of raid devices and such. tore is my username, md0 is the raid-array I use, level=5 is raid5 vs. for example raid1 which is level=1, raid-devices=3, the number of partitions dedicated for this specific array. /home/tore/raid is where i mount my array.
REMEMBER THIS GUIDE COME WITH NO WARRANTY, IF YOU LOOSE DATA DON'T BLAME ME. Try-it-before-you-buy-it if you can.

EDIT: I've edited the guide, I split the guide into three sections. (Prepare partition - make raid5 and format it - expand array & filesystem)

This guide have been tested with [COLOR="SeaGreen"]success on Ubuntu Feisty Fawn (7.04) 32-bit.[/COLOR]

If you test it on another system, tell me and i add a line above.

**[SIZE="3"]---Prepare the disk/partition---[/SIZE]**

What preparations needs to be done?
First you must know which partition/disk to use. I got no specific way of helping you here, best tips is to use gparted to get a graphic view of disks and partitions. 

gparted can be installed by:
```
sudo apt-get install gparted
```

To run gparted type:
```
sudo gparted
``` 

When you have sorted out which partitions/disks to use there are four things to do:
1.remove it from fstab
2.format it to ext3
3.set raid flag
4.unmount partitions

When you have figured out which partitions to use you can proceed to removing it from fstab. I assume you know how to do this, but a quick refresher if you don't remember the details:
```
Back up your fstab:

sudo cp /etc/fstab /etc/fstab.backup

edit your original fstab with gedit:

sudo gedit /etc/fstab

put a # in front of the line containing the partition you want to use. Save&Exit
``` 

Now its time for format the disks/partition to be used in the array. This is also a very straight forward kind of operation. Just run gparted again.
```
sudo gparted
```
Since gparted is graphical I cant give you a command line guide. But if you could find your way in fstab you should be able to navigate you way to your partitions in gparted with ease. Once there just right click it and format to ext3. Remember to be sure to pick the right partition, if you pick the wrong one there is no going back. 
After the partition has been formated right click it and &#8220;manage flags&#8221;, then hook-on the raid flag. Click "OK" & Exit.

The last step, make sure to unmount the partitions to be used in the array. Now they should be out of the fstab, this could be done via a reboot or:
```
sudo umount name_of_device

eksample:

sudo umount /dev/sda1
```
 
When this is done on all disks/partitions that are suppose to be a part of the initial array you are finished with preparing the disks/partitions. 

[SIZE="3"]**----Make softraid section----**[/SIZE]

Install mdadm (softraid driver/application):
```
sudo apt-get install mdadm
``` (awnser a few questions, i choose: none - yes)

Create raid device with partitions you prepared in gparted(modify this line for correct number of raid-devices and make sure to use the right devices):
```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```

The prosess of creating the array takes time, monitor it and do not continue this guide until its done(type it over again to update):
```
cat /proc/mdstat
```

Make a ext3 filesystem that spans the array:
```
sudo mkfs.ext3 /dev/md0
```

Mount the array (remember to choose were):
```
sudo mount -t ext3 /dev/md0 /home/tore/raid
```

Take ownership (replace tore with your username and correct the path)
```
sudo chown -R tore:tore /home/tore/raid
```

[optional]
The copy some files with valid sfv and check to see if everything is ok, and to have a refrence point after expansion.
```
cd /home/tore/raid
```
```
cksfv -r -q
```
[/optional]

[SIZE="3"]**----Expand section----**[/SIZE]
Unmount the array, i don't know if this is necessary, but doing so means less stuff to go wrong. 
```
sudo umount /dev/md0
```

Then you need to go and prepare the disk(s) to be added. (The prepare section of the guide)

Then tell mdadm that it can play with it:
```
sudo mdadm --add /dev/md0 /dev/sda2
```

Then tell mdadm to stop playing and use it to expand/grow your raid5 array(make sure that the number of raid devices is correct, it should be the number of disks/partitions the grown/expanded array will have):
```
sudo mdadm --grow /dev/md0 --raid-devices=4
```

View and wait for the new array to reshape:
```
cat /proc/mdstat
```

Check the filesystem (required to resize it):
```
sudo e2fsck -f /dev/md0
```

Resize the filesystem on the new array so that you can use it for something useful.
```
sudo resize2fs /dev/md0
```

Mount the expanded/grown array with it's resized filesystem(remember to change the mount point):
```
sudo mount -t ext3 /dev/md0 /home/tore/raid
```

[optional]
Go check your files:
```
cd /home/tore/raid
```
```
cksfv -r -q
```
[/optional]
_____________________
Need to expand more? Repeat the expand section. Remember to change number of raid devices and choose the correct device to add. Also, you can add more then one disk at the time, I jump strait from 3 to 6.
_____________________
Was this not the right guide for you? Try one of these (my guide is composed from some of these):

[http://scotgate.org/?p=107](http://scotgate.org/?p=107)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://linux.about.com/library/cmd/blcmdl8_resize2fs.htm](http://linux.about.com/library/cmd/blcmdl8_resize2fs.htm)
[http://www.mail-archive.com/linux-raid@vger.kernel.org/msg08539.html](http://www.mail-archive.com/linux-raid@vger.kernel.org/msg08539.html)
[http://ubuntuforums.org/showthread.php?t=509388&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=509388&highlight=mdadm)
[http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mdadm8.html](http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mdadm8.html)

EDIT1: Fix a buch of typos.
EDIT2: Split the guide into three sections, added some info on fstab, fix more typos.

---

### Post by tuckie on 2007-09-21
Just wanted to say thanks for the writeup, the bulk of it I knew, but its nice to have it all in one place.  I'm going to be using this on Monday.

---

### Post by tuckie on 2007-09-23
Quick question, anyone know if it is necessary to umount the raid volume before growing?  I'd rather not have to go through 7 hours of downtime.

---

### Post by tuckie on 2007-09-24
well im growing it without umounting the volume. Wish me luck.  Only 13 hours remaining!

---

### Post by matthodge on 2007-10-08
How did it go tuckie? RAID up and running without unmounting?

---

### Post by tuckie on 2007-10-08
well if you looked at my other posts you'd get a good idea :(  Essentally, growing the raid went fine, but I had to unmount it to grow the ext3 partition.  Pretty much  5 hours after everything was up and working, one of the drives dropped from the array and somehow the partition got corrupted in the process (2tb of data gone!).  

--Live and learn and always have backups.

---

### Post by ubdime on 2008-11-09
I've done this twice. From 4 to 5 disk raid5, then 5 to 6. It was online and mounted the entire time. Here is my log from 5 to 6.

The mdadm --grow took about 10-12 hours. And the resize2fs took a bit under 30 minutes. While it's growing, you can use watch -n3 cat /proc/mdstat to watch its progress. And while it's doing the resize2fs, you can use watch -n3 df to watch. Also I should mention that while it was doing all this, I even downloaded a few gigs worth of stuff and was heavily reading from the raid the entire time (seeding 500+ torrents with about 5-10 of them active at any given point and watching shows/movies from it).

root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd1[0] sde1[4] sdb1[3] sdc1[2] sda1[1]
      1953535744 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
md0 : active raid1 sdg1[0] sdh1[1]
      243167744 blocks [2/2] [UU]

unused devices: <none>

root@lanfear:~# mdadm --add /dev/md1 /dev/sdf1
mdadm: added /dev/sdf1

root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf1[5](S) sdd1[0] sde1[4] sdb1[3] sdc1[2] sda1[1]
      1953535744 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
md0 : active raid1 sdg1[0] sdh1[1]
      243167744 blocks [2/2] [UU]
      
unused devices: <none>

root@lanfear:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Fri Oct 31 23:10:19 2008
     Raid Level : raid5
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 6
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Nov  8 16:49:59 2008
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f6e524b8:284a0034:0f20f41d:3c651377 (local to host lanfear)
         Events : 0.324790

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       17        3      active sync   /dev/sdb1
       4       8       65        4      active sync   /dev/sde1

       5       8       81        -      spare   /dev/sdf1

root@lanfear:~# mdadm --grow /dev/md1 --raid-devices=6
mdadm: Need to backup 1280K of critical section..
mdadm: ... critical section passed.

root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf1[5] sdd1[0] sde1[4] sdb1[3] sdc1[2] sda1[1]
      1953535744 blocks super 0.91 level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      [>....................]  reshape =  0.0% (81280/488383936) finish=800.8min speed=10160K/sec
      
md0 : active raid1 sdg1[0] sdh1[1]
      243167744 blocks [2/2] [UU]
      
unused devices: <none>

root@lanfear:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf1[5] sdd1[0] sde1[4] sdb1[3] sdc1[2] sda1[1]
      1953535744 blocks super 0.91 level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      [===================>.]  reshape = 99.9% (488369920/488383936) finish=0.0min speed=19503K/sec
      
md0 : active raid1 sdg1[0] sdh1[1]
      243167744 blocks [2/2] [UU]
      
unused devices: <none>

root@lanfear:~# resize2fs /dev/md1
resize2fs 1.41.3 (12-Oct-2008)
Filesystem at /dev/md1 is mounted on /media/save; on-line resizing required
old desc_blocks = 117, new_desc_blocks = 146
Performing an on-line resize of /dev/md1 to 610479920 (4k) blocks.
The filesystem on /dev/md1 is now 610479920 blocks long.

root@lanfear:~# df | awk /md1/
/dev/md1             2403601996 1117790744 1285811252  47% /media/save

---

### Post by zorrek on 2008-12-12
I've done this twice. Both times, 4 disk RAID5 to 7 Disk RAID5, all 500 Gig drives.
Both times took just over 4 days to grow the array. Both times the arrays were on-line. Neither array was actually used while it was grown.
ext3 took 20 minutes to resize, again while on-line but not used.

---

### Post by roob85 on 2009-06-30
just wanted to say thanks for this great how-to. I used it to set up my first raid5 setup a few months back and im about to use it again to grow my array!

---

### Post by Fredrik_b on 2010-06-30
greate article, but I cant manage to execute the command "sudo resize2fs /dev/md0" without gettign the error message:

```


[root@localhost ~]# sudo resize2fs /dev/md0
resize2fs 1.40.8 (13-Mar-2008)
resize2fs: Device or resource busy while trying to open /dev/md0
Couldn't find valid filesystem superblock.

```

---

### Post by thenicnet on 2010-10-04
Tested in Ubuntu Server 10.04.1 LTS.  Went fine.

Ran into an issue after I restarted though, device md0 was gone.
Had to run:
[I]sudo mdadm --assemble --scan

[/I]Then:

*sudo mdadm --detail --scan*
It kicked back: 
[B]ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=18750866:7ef53616:aed1a40b:ef33f2e6
[/B]
Had to copy that, and paste it in the /etc/mdadm/mdadm.conf file.

Hope that helps, thanks for the write up.  I did exactly what you did, only with TB drives.

---

### Post by sgw86 on 2010-10-06
> **thenicnet said:**
> Tested in Ubuntu Server 10.04.1 LTS.  Went fine.

Ran into an issue after I restarted though, device md0 was gone.
Had to run:
[I]sudo mdadm --assemble --scan

[/I]Then:

*sudo mdadm --detail --scan*
It kicked back: 
[B]ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=18750866:7ef53616:aed1a40b:ef33f2e6
[/B]
Had to copy that, and paste it in the /etc/mdadm/mdadm.conf file.

Hope that helps, thanks for the write up.  I did exactly what you did, only with TB drives.

Thanks for the tip above! I restarted my machine and my array was gone!!

Where do i paste the ARRAY information that you get from --detail --scan into the mdadm.conf file??

---

### Post by zeroverse on 2010-10-11
[Moved to another thread]

---

