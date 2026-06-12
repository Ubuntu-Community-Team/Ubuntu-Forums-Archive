---
title: "Raid (md0) wont mount automatically during boot"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by edgicat on 2012-01-16
Hello,

This is my 1st post, so please be kind to me.

I'm running Ubuntu 64Bit 11.10 (upgraded from 11.04) installed on an IDE hard drive and I've created (after a bit of effort) a multi-disk software mirror raid consisting of 2x2TB SATA hard drives which I store all my data on, the only remaining issue I have is that the raid won't mount during boot.  This did not bother my until I just spent the whole weekend trying to create a samba share on my data raid too share files with my two android devices. I have finally come to the conclusion that the samba file sharing issue is being caused by the original data raid not mounting during the boot process.

Thus far after googling and finding a similar post of this site (unfortunately the other persons PC motherboard has died) It appears in 11.10 you have to configure which drives (other than the OS drive) are mounted automatically, this can be done by editing fstab in gedit or using a gui called "Pysdm".

Am i right in believing that fstab is still used to mount md software raids or do i need to reconfigure mdadm.conf (which is what i believed when i was using 11.04) or both?  

Can anyone confirm if the pysdm gui supports software raids?

I'm ready to be guided by you to resolve my issue.

Thanks in advanced

Edgicat

P.S. My Data raid has lots of files on it and I do not have another backup. The whole reason for me building the mirror raid in the 1st place was to act as a back up against hard drive failure etc.

---

### Post by edgicat on 2012-01-17
Ok, I was hoping for some answers or questions. I've added some addtional config information below. I hope this helps you to help me sort this mess out

Below is the details of my fstab config

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
#/dev/md0        /mnt/data       ext4    auto,users,rw,realtime 0       0

# swap was on /dev/sda5 during installation
UUID=4fc454ea-74b4-400f-a725-5afe1139c8e8 none            swap    sw              0       0

I've hashed out the "dev/md0" line as this does not mount my raid successfully, it also prevents me mounting it manually as well.

Here is a list of my UUIDs:
/dev/sda1: UUID="bf3926e8-6869-4e4a-bef7-d96dc212b651" 
/dev/sda5: UUID="4fc454ea-74b4-400f-a725-5afe1139c8e8" 
/dev/sdb1: UUID="667fbdc3-4c99-65c2-7349-3db790320375" 
/dev/sdc1: UUID="667fbdc3-4c99-65c2-7349-3db790320375" 
/dev/md0: UUID="b9a73224-0677-463d-aa59-53c86240f1c2" 

Below is the contents of my mdadm.conf:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=667fbdc3:4c9965c2:73493db7:90320375 name=solid-GA-MA74GM-S2H:0

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# This file was auto-generated on Mon, 29 Aug 2011 02:17:26 +0100
# by mkconf $Id$

---

### Post by edgicat on 2012-01-18
Don,t want to seem ungrateful, but is there anyone out there that can help me

---

### Post by Gone fishing on 2012-01-18
Can you manually mount the raid after boot?

What does cat /proc/mdstat
or
mdadm --detail /dev/md0

give you as an out put?

---

### Post by edgicat on 2012-01-19
Yes i can mount after boot, I've been using the Disk Utility GUI, which seems to mount as /media/raid. Info you requested below.

I've changed fstab last night

From:
/dev/md0 /mnt/data ext4 auto,users,rw,realtime 0 0

To:
/dev/md0 /mnt/data ext4 defaults 0 2

Which now allows the raid to mount during boot, I don't know if it was the defaults or changing the pass from 0 2 which fixed the problem, I don't really understand what the pass variable does, other than its something to do with file system checking.  How does changing the number effect the mounting process and can you have the same pass number for different drives?

Although the raid now mounts an icon (shortcut) is not created in Nautilus under computer, in the same way file system drive does.  Thus far i've created a bookmark to it because i can not see anyway of adding icons to the computer section.

Have i mounted the raid incorrectly?
Do i need to change something else for Nautilus to show the raid as a drive icon?

Although My folder share settings (on the raid drive) are now being remembered, I'm still unable to access the samba share I've setup for that folder. 

cat /proc/mdstat:
md0 : active raid1 sdb1[0] sda1[2]
      1953510841 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>


mdadm --detail /dev/md0:
/dev/md0:
        Version : 1.2
  Creation Time : Mon Aug 29 02:03:09 2011
     Raid Level : raid1
     Array Size : 1953510841 (1863.01 GiB 2000.40 GB)
  Used Dev Size : 1953510841 (1863.01 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Jan 19 07:41:47 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : solid-GA-MA74GM-S2H:0
           UUID : 667fbdc3:4c9965c2:73493db7:90320375
         Events : 802

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       2       8        1        1      active sync   /dev/sda1

---

### Post by Gone fishing on 2012-01-19
Sorry travelling and not able to respond earlier.

Looks to me like a UUID problem i.e you original fstab had the wrong UUID as it mounts with /dev/md0. I also note that the UUID in your fstab is different to the one that mdadm --detail /dev/md0 gives.

have a look at [https://bbs.archlinux.org/viewtopic.php?id=61758](https://bbs.archlinux.org/viewtopic.php?id=61758)
and
[http://ubuntuforums.org/showthread.php?t=1503641](http://ubuntuforums.org/showthread.php?t=1503641)

---

### Post by edgicat on 2012-01-19
Thanks for the response

Um the UUID in my fstab relates to my swap partition on sda5, although I take you point ref blkid and mdadm not showing the same UUID.  How strange.

After looking as the 1st link you sent i added the following:

ARRAY /dev/md0 level=raid1 num-devices=2 metadata=1.2 UUID=667fbdc3:4c9965c2:73493db7:90320375

to my mdadm ans rebooted.

blkid still shows the same UUID and i'm still accessing the mount via a book mark.

The second link you posted seems to indicate that the miss report of the UUID could be a bug (Or as they would say a work a feature) in the kernel, as for md[x] UUID's being completely different to filesystem UUID's, well I guess that's just life ;-).  I also read on another post that for Raids it was not recommend to mount via UUID

Have changed fstab to mount md0 by it label RAID and restarted pc, raid mounts as before still accessing raid via book Mark.

Tried changing rhetorically mount location from /mnt/data to /home, believing  that it would then mount inside thwarting home folder and thus allow raid to be accessed via home instead of a bookmark.  Pc now won't login or shut down for that matter.

Time for bed me thinks, looks like i have something else to fix now oops

---

### Post by Gone fishing on 2012-01-20
OK I now know why blkid and mdadm --detail --scan give different UUIDs (see below) but I'm not sure which you should use in fstab.

However, I can't see why you shouldn't use /dev/md0 in your fstab rather than the UUID of the raid. Obviously the advantage of UUIDs comes into play when plugging flash disks, hardrives into a system and the box getting confused at to what is sda sdb etc, but that's not going to happen with a raid, as you are not going to plug in another raid device.

[http://arstechnica.com/civis/viewtopic.php?f=16&t=67783](http://arstechnica.com/civis/viewtopic.php?f=16&t=67783)
[http://www.mentby.com/tom-h/mdadm-and-uuids-for-its-component-drives.html](http://www.mentby.com/tom-h/mdadm-and-uuids-for-its-component-drives.html)

---

### Post by louix on 2013-01-29
The blkid ID's worked for me. The one given by adadm scan did not.

---

