---
title: "Ubuntu installed.....where ?"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2014-01-04
A silly question you may think...i will make this as easy as i can

I just rebuilt my old PC. I decided to dual boot with Win 7 & Ubuntu (Win XP & Ubuntu before). I wiped the HD (Main Disk) and also installed another HD that i was just going to use as a Data Disk to store pictures, films etc...(Both disks are only 80GB).

I installed Win 7 no problem, and that is working, so then i went for Ubuntu. It all seemed to go fine, and when given the option i asked it to install it beside Win 7 (then Both systems should be able to access the Data Disk).

Now here is where i am confused. I know Win 7 is on my my Main Disk. When i am in WIn 7 it tell me my Data disk is only 40GB now ?? When i look on there i can find a few files i have put there, so somewhere it has lost the other 40gb of space?? 

**BUT** if i go into Disk Management in Win 7 i have 3 partitions now on my Data Disk

1 of 40gb (approx)
1 of 35gb (approx)
1 of 2gb (approx)

Am i presuming right that it has installed Ubuntu into one of those 2 large partitions on my Data Disk and not along side Win 7 on the Main Disk ??

Its ts not a major issue, just means i cannot use that whole disk for Data as i wanted....or i could unplug that disk and re-install Ubuntu then it would have to put it along side Win 7 on the Main Disk.

Can someone please confirm if my thinking is correct. Any help would be great :)

---

### Post by The Cog on 2014-01-04
The windows disk thingy doesn't really tell you what's happening - sometimes omitting things and sometimes outright lying. Can you boot Ubuntu (or the live CD) and post the output of the command ```
sudo parted -l
```

---

### Post by MadMonkey1966 on 2014-01-04
Thanks for the quick reply....I am in Ubuntu now.....here is what i got back 

Model: ATA ST380013AS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   80.0GB  79.9GB  primary  ntfs


Model: ATA Maxtor 6Y080M0 (scsi)
Disk /dev/sdb: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.5GB  43.5GB  primary   ntfs
 2      43.5GB  82.0GB  38.5GB  extended
 6      43.5GB  79.8GB  36.4GB  logical   ext4
 5      79.8GB  82.0GB  2145MB  logical   linux-swap(v1)

---

### Post by Impavidus on 2014-01-04
Windows is on the entire first drive, Ubuntu on the second half of the second drive. You haven't done anything with your system yet (so, no valuable data). The way to fix this is to boot Windows, shrink the C partition to about half the drive (or whatever it needs, I'm not really familiar with Windows) and defragment a few times (not really sure about that, but it can't hurt). Then boot the live disk, remove the existing Linux partitions using gparted and create Linux partitions on the first drive. Then, install and go for manual partitioning (select "Something else"). This way you can be sure the installer won't put Ubuntu on the second drive. Also format the second drive as ntfs partition.

You can also wipe the second drive and unplug it. Then you can be sure Ubuntu won't be installed there, the automatic option ("Install alongside") will the the right thing then. Finally plug the second drive in again.

---

### Post by MadMonkey1966 on 2014-01-04
Many Thanks Impavidus, i was looking at the output from the Terminal and that is what i figured \\:D/

I htink i will take the second option, just unplug the Data Disk, then just run the live cd again and then it will end up where i want (like it was with XP before).

I am learning slowly.

Many Thanks again to yourself and The Cog ):P

---

### Post by deadflowr on 2014-01-04
You're basically right about Ubuntu being installed on one of the two partitions.
It's within the 35Gb partition you listed(of the three).
It happens that Windows can see both the extended partition and the swap partition, but not the ext4 partition.
Both the swap and the ext4 partition are within the extended partition.
/dev/sdb2 is the extended.
/dev/sdb5 is the swap.
/dev/sdb6 is the ext4.
Ubuntu is on /dev/sdb6.
And of course Win7 is on /dev/sdb1.

Don't know if that's at all helpful.
Kinda got lost on what the question was...

---

