---
title: "How to  resize  Ubuntu 18.04 Partition  on Dual Boot Windows 10"
date: 2019-12-10
forum: New to Ubuntu
---

### Post by zash1957 on 2019-12-10
I have Dual booted Ubuntu 18.04 on my C Drive alongside Windows 10  Allocated 25G to Ubuntu., and now want to increase  to 100G.. my C drive has 300G allocated freespace... I am unsure as how to do this, as I tried partitioning  on Windows but it would not let me increase my Ubunto partition ... I have downloaded Gparted from ubuntu software  on my Ubuntu OS... but i am still unclear as how to do it.


Any help for a Newbie Ubuntu user would be most grateful.

Thanks in Advance

---

### Post by yancek on 2019-12-10
Boot Ubuntu, open a terminal and run the below command and post the output here.  It's a lower case Letter L in the command.

```
sudo parted -l
```

There is a difference between having unallocated space which in not included in any partition and having free space in a partition.  Which is it with windows?  The above command will show that.  You won't be able to use GParted on the installed Ubuntu because it will not resize a partition in use.  You could use the DVD/USB you used to install Ubuntu as GParted is on it.  Using GParted is explained in detail in their manual which is at the link below.  

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by zash1957 on 2019-12-10
Yanek .. thanks for the quick reply 

Unfortunately the free space is also on my C drive on windows 10.

I have the read the link you attached (thanks for that).. again my problem is everything is on my C drive... not my partition for ubuntu.

is there a way to delete my  unbuntu partition  without losing the data on it and then make a bigger partition and keep the existing data.... or just reinstall ubuntu and start all over again.  and lose my existing settings on ubuntu.

Sorry to be such a pain and a computer idiot.

here is the data you requested....

Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  501GB   501GB   primary   ntfs         boot
 2      501GB   528GB   26.2GB  extended
 5      501GB   528GB   26.2GB  logical   ext4
 3      528GB   1000GB  473GB   primary   ntfs

---

### Post by TheFu on 2019-12-10
Making the ext4 partition larger will be a pain, but you can reduce either of the Windows/NTFS partitions in size, create a new partition in that empty space, format an ext4 file system, then use it inside Ubuntu.

Any shrinking of Windows partitions should be done in Windows.

BTW, "C: Drive" isn't technically accurate.  It is a "C: partition" and it appears you also have a D: partition.

25G is a good size for an Ubuntu OS.  So I'd make the new partition used for /home/.
If you are afraid of any data loss, and you should be, then make a backup of anything you don't want to lose.  It is very common for someone new to partitioning and file systems to make a mistake, wiping out everything.

Please make a backup before starting.  Please.

---

### Post by C.S.Cameron on 2019-12-10
> **TheFu said:**
> 

Any shrinking of Windows partitions should be done in Windows.




+1 (Using Manage).

---

### Post by yancek on 2019-12-11
> is there a way to delete my  unbuntu partition  without losing the data on it  

No.  Interesting that you have windows 10 on a Legacy/msdos drive.  Question is, what's on partition 3 which shows as a 473GB drive?  Is that a data partition?  You don't seem to have the standard recovery partition windows uses so...?

It should be possible but it's going to be convoluted and you might be better off trying to save your data and setting and reinstall.  You could use windows Disk Management to either shrink partition 3 at the end of the drive, moving it to the right to create additional room for Ubuntu.  THis will take some time as it will probably need to move all the data also (not sure what's on that partition.  After moving this partition to the right, you could use GParted from the Ubuntu install media to move the Ubuntu partition to the right to take up the newly created unallocated space.  Make sure the Ubuntu partition is NOT mounted before doing this.

OR, shrink the windows system partition (partition 1) again using Disk Management in windows.  This might be simpler as it will be moving the partition to the left and there probably is not data at the end of the partition so it should be faster.  After doing this, again boot the Ubuntu install media and use GParted and unmount partition 5 then unmount partition 2.  You could then move partition 2 (Extended partition) to the left to use up the unallocated space, after doing that, move partition 5 to the left also to use up the unallocated space.

---

### Post by zash1957 on 2019-12-11
TheFu

Thanks for your advice.

 I understsand that i need to do any resizing in Windows.. but i do not know how to [COLOR=#000000] format an ext4 file system, then use it inside Ubuntu.... I am a complete novice on the tech side of things. ... in my windows system my ubuntu  partition is on my C drive, but I also have a complete empty hard drive, my D drive... of 500gb.. is there any way i can transfer my C partition and move it to my D drive  and use that as my ubuntu system ?[/COLOR]

---

### Post by yancek on 2019-12-11
Just saw your last post.  Formatting a Linux partiition ext4 or any other filesystem type can be done during the installation but this means an end/loss of any data on that partition.  You can also do it from GParted on the Ubuntu install media.

> [COLOR=#000000]in my windows system my ubuntu  partition is on my  C drive, but I also have a complete empty hard drive, my D drive... of  500gb.. is there any way i can transfer my C partition and move it to my  D drive  and use that as my ubuntu system ?[/COLOR]

The output of  the parted command you posted above shows only 1 drive of 1TB (1000GB), with the older Legacy/msdos drive with your Ubuntu installed on a Logical partition within an Extended partition andd is not on your C partition.  Moving the windows install to another physical drive is a question you'd be better off asking at  windows forum.

---

### Post by TheFu on 2019-12-11
I don't think you have 2 drives.  I think you have 2 partitions - C: and D:.  Windows calls these "drives", which is completely incorrect, inaccurate, wrong.

If it were me, I'd resize the last partition to free up space either before or after the last partition. This is outside the Extended partition.  Then I'd take that free space, create a primary partition inside it, then create an ext4 file system into that partition.  After you do this, come back for next steps.

There is only room for 1 more primary partition. This is a limitation of using MBR/MSDOS partition tables.  This is also required by Windows because it isn't use UEFI to boot, so you can't use a much more flexible GPT partition table which has basically unlimited partition support.

The extended partition is sized only 26G and fully used by Linux.  I have no idea how this happened or why. Seems really funny.  Unfortunately, resizing the *extended partition* isn't allowed if there is any *logical partition* inside them.
> 
If you are afraid of any data loss, and you should be, then make a backup of anything you don't want to lose. It is very common for someone new to partitioning and file systems to make a mistake, wiping out everything.

Please make a backup before starting. Please. 

I want to be very clear. This stuff can be risky to all your data on the disk. Windows and Linux. All of it.

---

### Post by CatKiller on 2019-12-11
> **TheFu said:**
> Unfortunately, resizing the *extended partition* isn't allowed if there is any *logical partition* inside them.

That's not true. You can't move the boundaries of the extended partition container past the boundaries of the logical partitions inside, obviously, but you can move either end through unpartitioned space, and you can slide logical partition start and end points around within the extended partition. You just need none of the partitions to be mounted. And it might take a very long time when you're moving start points.

Agreed on the need for backups, and that both Windows and MBR make this more of a pain than it could be otherwise.

---

### Post by TheFu on 2019-12-11
Had I not just attempted this 2 weeks ago, I'd have a different stance. Perhaps it is a newer capability that doesn't work on my LTS releases?  I ended up repartitioning the disk to the way I wanted and restoring from backups, which took about 26 hrs for that amount of data.

---

### Post by hk42 on 2019-12-11
I don't agree on using Windows to shrink its own partition.
It is worth trying but as the partition is mounted sometimes it doesn't work
or only allows to free a few MB when there is a lot of unused space.
In such cases Gparted on a live USB disk worked for me but it warned me it could be unsafe and it took a lot of time.
May be a Windows defragmentation could have helped but it seems gparted is clever enough to do it.
A good idea is also to use the Windows function to free disk space before using gparted.
Having big boot partitions is not a good idea for any OS for backup reasons.
Linux with mount-points and symbolic links is very flexible on that point.

---

### Post by C.S.Cameron on 2019-12-17
I had good luck using AOMEI, (free), to partition a Windows drive when Windows couldn't handle it.
I have had problems in the past using GParted on a Windows drive. Besides it can take a long time.

---

### Post by oldfred on 2019-12-17
While I normally recommend Windows tools for Windows, its partitioning with BIOS/MBR and Linux logical partitions has a bug going back to Windows 7 but still present with Windows 10 when BIOS/MBR.
It conveniently "forgets" to include the Linux logical partitions when it rewrites the partition table. Data is still there, but partition table entry is missing.
Recently someone using AOMEI has same issue.

Issue with Windows is that is needs defrag & turning off fixed files like the hibernation file first or MFT master file table. Many have used gparted, but those that have had issues then blame Linux. Probably would have had issues with Windows as some partition issue, but that is why we normally suggest using Windows tools to shrink NTFS partitions. And gparted for just about everything else.

One of many where Linux partition disappeared.
       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &

---

### Post by TheFu on 2019-12-17
> **oldfred said:**
> ...  Many have used gparted, but those that have had issues then blame Linux. Probably would have had issues with Windows as some partition issue, but that is why we normally suggest using Windows tools to shrink NTFS partitions. 

Exactly this. 

Send people to Windows to do Windows things, then when that fails, they come back, understand it is non-trivial, can cause total data loss, then try using one of the many Linux-based partitioning tools.  If Windows breaks something first and Linux lets them recover something, anything, or even fully, magically, Linux isn't so bad.

If Linux doesn't help at all, then the probably was too far gone already - obviously true since Windows didn't help either.

For experienced Linux people, 1st they know and have backups.  They are willing to wipe everything and reload using those backups.  Great backups are extremely freeing.  I don't worry about hardware failures, hardware being stole, dumb mistakes, viruses, or malware. 

Needing to resize partitions can take more effort and downtime than wiping everything, installing fresh and restoring from good backups.

Good backups have 1001 uses, not just the obvious list.  Sleeping well at night is one of those uses too.

---

