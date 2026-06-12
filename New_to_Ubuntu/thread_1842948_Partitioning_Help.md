---
title: "Partitioning Help"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by TDalton on 2011-09-12
I am using an Asus laptop

I have installed Ubuntu 11.04 and gave it its own partition on my hard drive. During the installation, I moved my files from windows to Ubuntu. They are located on my OS /media

In these files are my old 'my documents' stuff. I want these in my /home folder.

My /home folder doesn't have enough room. I figured this was because the partition size was too small. 

I have backed up everything I needed and went ahead and used OS-Uninstaller to remove Windows 7 and WIndows recovery. I am happy they are gone.

GParted shows me a number of partitions. A screenshot is below. I am unfamiliar with this part. Which partition is my /home? How do I enlarge this partition? Is there a risk of file loss from making one partition larger and one smaller?

Thanks for any help.

---

### Post by sanderd17 on 2011-09-12
can you show us the content of your /etc/fstab file in Ubuntu?

please put it between CODE tags.

---

### Post by saltmarshlamb on 2011-09-12
That doesn't show which is /home. Open a terminal and run 

```
cat /etc/fstab
mount
```

---

### Post by FormatSeize on 2011-09-12
None of them are your /home partition. You have to create that as a seperate partition during the installation process.
 
Too, while you have deleted Windows, you failed to shrink the partitions it lived on. So the partition formatted as "NTFS" is where Windows used to live. You should shrink that partition, and make the 7 Gig, and the two 3 Gig partitions larger (probably much larger). Currently, your Ubuntu installs are on partitions smaller than many standard USB drives.

---

### Post by TDalton on 2011-09-12
These are the contents of /etc/fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f76c2eb4-452a-47b1-859c-248922c16ca7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=b1974f2b-8f30-4352-94c8-4a5255a341c8 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

I tried running the recommended code, and from what I read, its the same as above. 

The partition entitled NTFS should be 'shrunk' or 'removed'? Also, does it matter how large I make the partitions? What would folks recommend?

---

### Post by sanderd17 on 2011-09-13
Ok, in the fstab file, you can read that sda5 is your root partition with everything in it (including your /home).

sda6 should be your swap, but gparted says there are errors with it. Maybe it would be best to reformat sda6 as swap. For the case you don't know what swap is, swap is an extension of your RAM memory on your HDD. So it's emptied every shutdown (just as your RAM is empty when your computer is powered off). So reformatting swap is not dangerous.

for the rest, the fat32 and ntfs partitions are windows partitions.

To remove windows, you can delete the partitions sda1 and sda2. Watch out: this will remove every file on that partition. So make sure all your files are on your Linux partition before you start.

If you deleted those, you can enlarge the extended partition sda3 and afterwards enlarge sda5.

Watch out: do one job at a time (e.g. delete sda2 and apply the changes with the green V). It can take a long time to apply the changes (last week, I enlarged a 200GB partition with 100GB data to a 300GB partition and it took about 6 hours). 

DO NOT INTERRUPT GPARTED

If you interrupt gparted, you are likely to lose everything on the partition that was being edited.

---

### Post by oscarivera9 on 2011-09-13
If at all possible, save all of your important files that you had in "My Documents" on to an external drive.  What you've got here is a big mess that although it can be fixed, you still run the chance at having everything deleted by accident anyway.  What I would do if I were you, (excuse me, what I have done in the past in a similar situation) would be to start fresh and reinstall Windows 7 but on a primary partition under 100GB.  Then I would format a FAT32 primary partition of about 200GB which is where I would store all of my documents.  Both Linux and Windows can read and write onto a FAT32 partition, so you can easily access files in a FAT32 partition regardless of which operating system you are using.  Finally create an Extended Partition with the rest of the drive.  Out of this extended partition create two logical partitions and use 4GB for the Swap partition.  Then use the rest as an Ext. 4 partition for a fresh install of Ubuntu.  
Let me explain why I would go with this:
 I don't know how long you have been using Linux.  If you have been using Linux for longer than a year and you've decided that you no longer need Windows then go ahead and skip the Windows 7 installation.  However, if you've been using Linux for less than a year there's a good chance that you'll come across someday when you'll wish you had Windows.  When that day comes and you decide you are going to install it you'll have no choice but to install it after Ubuntu, which is a bad idea.  People here will tell you that it's best to have Windows installed first and Ubuntu next.  Windows (especially Windows Vista and Windows 7) like to think that Linux doesn't exist and when they(Windows) get installed on a PC that's already running Linux, they cause a lot of problems.  However, when Windows is installed on the first part of the hard drive and Linux goes after that, things work out all right.

---

### Post by sanderd17 on 2011-09-13
> **oscarivera9 said:**
> would be to start fresh and reinstall Windows 7 but on a primary partition under 100GB.
I believe he said that he doesn't need Windows anymore

Anyway, making a backup of your files on an external disk is always good. As I said, if you interrupt gparted (or it fails because of a power problem or so), you will likely lose all files on that partition.

---

