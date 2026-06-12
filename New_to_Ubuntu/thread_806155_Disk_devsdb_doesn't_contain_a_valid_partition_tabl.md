---
title: "Disk /dev/sdb doesn't contain a valid partition table"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by 449 on 2008-05-24
Is my external hdd broken? I've tried formatting it but nothing changes...

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b00fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2898    23278153+   7  HPFS/NTFS
/dev/sda3            2899       38848   288768375   83  Linux
/dev/sda4           38849       38913      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000166a

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by HotShotDJ on 2008-05-24
> **449 said:**
> Is my external hdd broken? I've tried formatting it but nothing changesWhat method are you using to partition and format the drive?

---

### Post by 449 on 2008-05-24
> **HotShotDJ said:**
> What method are you using to partition and format the drive?

gparted, I've tried everything I know of.

---

### Post by HotShotDJ on 2008-05-24
> **449 said:**
> gparted, I've tried everything I know of.I imagine that when you plug in the external drive, it is not automounting and showing up on your desktop or in "Places" since there is not valid filesystem on it.  However, could you confirm that for me?

---

### Post by |{urse on 2008-05-24
DONT DO IT THIS WAY IF ITS A THUMBDRIVE

but normally if you wanted to reformat and mount a hard disk:

sudo mkfs -t ext3 /dev/sdb

sudo su

mkdir /media/sdb

su yourusername

sudo mount /dev/sdb /media/sdb

sudo chown -R yourusername /dev/sdb

sudo chown -R yourusername /media/sdb

---

### Post by 449 on 2008-05-24
> **HotShotDJ said:**
> I imagine that when you plug in the external drive, it is not automounting and showing up on your desktop or in "Places" since there is not valid filesystem on it.  However, could you confirm that for me?

Yes, it shows up as /media/disk.

---

### Post by HotShotDJ on 2008-05-24
> **449 said:**
> Yes, it shows up as /media/disk.Ok.. Thats a horse of a different color.  If there were no file system on there at all, it would not mount.  So lets unmount the thing (right click on the desktop icon and then choose "Unmount" from the pop-up menu)

Now, you can run gparted on it.  Make SURE you are running it with Administrator privileges.  Delete any partitions on there already (I'm assuming there is no data on the drive that you wish to save).  Now, create the partition, define the filesystem you want to use and then apply.  Everything should go smoothly now.

---

### Post by 449 on 2008-05-24
> **HotShotDJ said:**
> rive that you wish to save).  Now, create the partition, define the filesystem you want to use and then apply.  Everything should go smoothly now.

Heres: what happen: I unmounted the drive, opened terminal, then typed 'sudo gparted. At this point it scans for devices and nothing happens.

---

### Post by HotShotDJ on 2008-05-24
> **449 said:**
> Heres: what happen: I unmounted the drive, opened terminal, then typed 'sudo gparted. At this point it scans for devices and nothing happens.:confused:
At the very least, it should be detecting your internal hard drive that is clearly there, or you wouldn't be able to boot your computer at all.

EDIT:  What happens if you type ```
sudo gparted /dev/sdb
``` or ```
sudo gparted /dev/sda
```NOTE:  With /dev/sda -- LOOK, but don't TOUCH!  :)

---

### Post by gruslo on 2009-01-28
I have the same issue (external hard drive not working, same message about not containing a valid partition) but I cannot unmount my drive and then "gpart" it, because when I right click on the drive, the option I have is to "mount" it and not to unmount. If I choose "mount" I get the message "Cannot mount drive". If I go to gparted and right click on the sdb drive to format it, I see that the option "Format" cannot be clicked cause it's inactive. How can I manage with this??

---

### Post by HotShotDJ on 2009-01-28
> **gruslo said:**
> I cannot unmount my drive and then "gpart" it, because when I right click on the drive, the option I have is to "mount" it and not to unmount. If I choose "mount" I get the message "Cannot mount drive".That's ok.  Just don't mount it.  It is already unmounted> **gruslo said:**
> If I go to gparted and right click on the sdb drive to format it, I see that the option "Format" cannot be clicked cause it's inactive. How can I manage with this??You must run gparted with administrator privileges.  Rather than clicking on it in your Applications menu, open a terminal (Applications --> Accessories --> Terminal) and type:```
gksudo gparted
```(I've noticed that in my older posts in this thread, I told the OP to use sudo... that was wrong :oops: )

---

### Post by The Cog on 2009-01-28
While it's mounted, use the command **mount** to see how it is mounted. My guess is that it's mounted as /dev/sdb, rather than sdb1 or sdb2 etc. If this is the case, the thumbdrive is formatted as you would format a single partition, rather than being formatted with a partition table at the front as you would with a hard disk. If it's not the case, ignore the rest of this post.

You can do this with Linux of course by using **sudo mkfs -t ext3 /dev/sdb** instead of **sudo mkfs -t ext3 /dev/sdb1**. 

Which way you choose to format it is up to you of course, but I think my preference would be to have it like a normal hard disk with a partition table at the front. If you want to put a partition table at the front, you will probably have to overwrite the existing filesystem header with zeros like this: 
**sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1**
 and double-check you are doing it to the right drive before hitting enter!
Then you should be able to create partitions with gparted.

---

