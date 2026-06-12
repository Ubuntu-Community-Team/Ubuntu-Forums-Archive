---
title: "[SOLVED] Hard Drives: RAID or storage?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Aiki on 2008-07-25
Hello, Ubuntu folks!  First time poster and user, long-time lurker here.  I've had Ubuntu for about a week now, and let me tell you - I LOVE it!  My friend and I have been enjoying trying to figure things out, and it seems to be working beautifully! I've got most everything set up for my usage, but I do have a few questions....

Here's my problem: I've got two SATA hard drives, same size and model.  However, my / is only **one** of these drives.  It seems the other one isn't being used!  

My questions are, first - can I RAID them together? If so, how? Secondly, if didn't want to RAID them together, could I somehow "add" the second hard drive as storage, or at least get my system to recognize it as free and available space?

Thanks for all the support! Again, glad to be here! Peace,

Aiki.

---

### Post by ConMan318 on 2008-07-25
[http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System](http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System)

Have a look at that; I just followed those instructions earlier today to configure my second hard drive as a slave drive.  If you're dead-set on RAIDing them together, wait for another poster, but these instructions work perfectly for a slave drive.

Glad you are enjoying your Ubuntu experience!

---

### Post by DGortze380 on 2008-07-25
Don't RAID.. IMO it's pointless, but realistically, there's very little benefit... and it's difficult to setup in linux anyways.  Just partition the second SATA drive, add it to fstab so it will auto-mount and use it for storage/backup. Check out the post above and this one.

[http://ubuntuforums.org/showthread.php?t=870059](http://ubuntuforums.org/showthread.php?t=870059)

---

### Post by bab1 on 2008-07-25
The simple answer to your questions is: Yes to both, but not at the same time ;-)  There are considerations to both questions.  

For RAID some thoughts are : do you want to use hardware RAID or software? How many disks in the RAID array?  Do you want to use RAID 0, 1 or 5?  If you use only the 2 SATA drives you will **not** gain any more storage capacity.  As you can see; many questions.

Using the second SATA as extra storage is much simpler.  format the disk with whatever partitions you want and you can mount them to the file system where you want.

I have resisted just giving you the howto solutions.  I can help with that, but you should google RAID and see what it does and why you use it.

Searching these forums for: fstab will get you some idea how to add a second hard drive to your system.

---

### Post by Aiki on 2008-07-25
Thanks to all the helpful input!

So, for my first thread, here's a story.  I went downstairs and said to my girlfriend, "I posted a thread at the beginning of Psych (a show we were watching), and I got a solution before the show was over." 

To that, she said, "There are bigger computer nerds than you?" 

Cheers to the bigger nerds. ;) 

<3 Ubuntu Community. Peace,

Aiki

---

### Post by PilotJLR on 2008-07-25
I have to respectfully disagree about RAID... it is EASY to setup in linux, and tremendously useful.

I have some small-business servers that run RAID 1... so they can keep plugging away after a drive failure.

My workstation, in contrast, uses RAID 0. This is risky, since it's basically a guarantee of data loss at some point in the future, so I backup nightly to a third disk. My primary volumes, though, are MUCH faster than a RAID 1 or single disk setup. This is easily noticable when I use the machine.

---

### Post by Aiki on 2008-07-25
Alright.  Figured it out, thanks for all the help again!

---

### Post by PilotJLR on 2008-07-25
Your new drive is already partitioned... you did that, right??

To see if it is mounted:
```

sudo mount | grep sdb1

```

If nothing comes back, then it is not mounted. If that's the case, then MAKE SURE you don't have data you want on this drive, and then make a file system on it, like so:
```

sudo mke2fs -j /dev/sdb1

```

** This command will ERASE EVERYTHING ON /dev/sdb1, so don't do that unless you are POSITIVE you don't hava data on there already. **


Afterwards, create a mount point and mount it:
```

sudo mkdir /new-disk
sudo mount /dev/sdb1 /new-disk

```




EDIT: I see you already determined it's mounted... so no action needed! The first command should then return the mountpoint, which you already know is /storage.
Of course, substitute "new-disk" for something less lame.  :-)

---

