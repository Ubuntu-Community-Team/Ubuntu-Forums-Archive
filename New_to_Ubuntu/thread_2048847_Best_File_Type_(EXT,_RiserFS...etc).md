---
title: "Best File Type (EXT, RiserFS...etc)"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-08-27
Hello everyone

I was wondering if I could get some advice on which is the best file system to use and a little bit of help in making a transfer happen.

1) I'm looking to replace my SATA HDD for a faster one. I'd like to put a new SATA HDD in my machine and basically copy everything from my "old" (existing) drive over, then remove the old drive. Essentially I'm looking to clone it into a new disc - not just copy some files over. I want the OS and everything because I have a lot of custom settings that would take me ages to do if I had to do a clean format.

2) I have an external USB 2.0 HDD that I use for backing up files. I back up a variety of files such as short movies, music albums (so multiple 2-10 minute sound files), images (both high and low res) and all the usual junk you find on your PC. What is the best file system to use for this? I would only be moving it between Linux machines, so it doesn't need to be a FAT file system for compatibility purposes.

(P.S. is it possible to change your file system once you've set up ubuntu, for instance, can I change my EXT HDD to something else? - just curious)

Thank you all

---

### Post by ratcheer on 2012-08-27
What you are asking is a huge question and you will probably get widely varying opinions. Here is mine.

If you want a fast, stable, easy to use filesystem right now, use **ext4**. If you want to be ready for the future and are willing to go through a learning curve, try **btrfs **or **zfs**. I think zfs may be a little more stable right now, but **btrfs **may be the best in the long run.

Many filesystems allow you to convert from other filesystems, but it is not universal. You need to do careful research before you install one filesystem with it in mind that you will convert it to another one, later. Look at the docs of the one you want to convert to to see which filesystems they allow you to convert from.

If your external drive ever needs access by Windows hosts, make sure to give it a filesystem that Windows can use, such as FAT32 or NTFS.

Again, these are just my opinions and they are worth very nearly what you paid for them. ;)

Tim

---

### Post by Cheesemill on 2012-08-27
1) I would recommend using [Clonezilla]("http://clonezilla.org/") to clone your drive.

2) Unless you have any specific needs that are not covered by ext4 (and you'll know if you have them) then go for ext4. It's mature, stable, and has good performance. The advantages of ZFS only really come into play if you are using multiple drives in a RAID-like setup. Btrfs is still experimental and isn't really ready for mainstream use yet.

As ratcheer said you will probably get a different reply from everyone that answers, but I'd be suprised if the general outcome isn't 'use ext4'.

---

### Post by Bashing-om on 2012-08-27
+1 on ext4 for day in day out desktop usage. For for a partition that does many many read/writes on small files, ReiserFS offers superior handling of many files within a particular directory and has excellent performance for these small files. Like others advise, lots of thought goes into how a system is to be partitioned for how it will be used and the corresponding file systems applied thereon.


[INDENT]for what it is worth <==BDQ  
[/INDENT]

---

### Post by oldfred on 2012-08-27
I think ext4 is first or second in every test and wins overall. Plus it is well supported with or by most repair/recovery tools.

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

If not using a full image clone, do not use NTFS or FAT as neither supports Linux permissions or ownership. Everything will be converted to root and cause major issues. If just data and you want compatibly with Windows use NTFS.

I am a believer in clean installs. Most of your settings are in /home so if you copy that you have your settings. A few hardware settings may also be in /etc.

---

### Post by LewisTM on 2012-08-27
Ext4 should be fine for regular use and/or for booting a system. For my home partition, media and backups, I opt for the robustness and performance of **XFS**.
[http://lwn.net/Articles/476263/](http://lwn.net/Articles/476263/)

Cheers!

---

### Post by Drowz0r on 2012-08-27
Thanks guys. Those are some really helpful replies.

What do you recommend formatting the USB external drive with? I've tried using "Disk Utility" but I just get errors so I don't think the tool is really meant for that... I think.

---

### Post by newb85 on 2012-08-27
+1 for ext4.

+1 for clean install.  But first, open Software Center, click "File>Sync between computers".  Once you have the clean install done, you can see everything you had installed before, and can simply click to install them again.  And as oldfred said, your settings should all be saved in your home directory.

---

### Post by ratcheer on 2012-08-28
> **Drowz0r said:**
> 
What do you recommend formatting the USB external drive with? I've tried using "Disk Utility" but I just get errors so I don't think the tool is really meant for that... I think.

Disk Utility *should *work. You have to make sure the device is not mounted when you try to format it.

If you still can't get Disk Utility to format it, try a dedicated tool such as gparted. Personally, I rely on the Parted Magic Live CD, but there are plenty of good partitioning tools available.

Tim

---

