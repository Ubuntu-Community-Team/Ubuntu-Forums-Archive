---
title: "how to repartition drives?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by 007casper on 2013-04-05
I would like to give more 3Gb to my file system.  
What is the best way to re partition via Gparted or terminal without corrupting any files?

At the time, I set the swap close to double the ram size. I have 14.93gb in swap section since I have 8gb ram. 

so far the way the hard drive is set up...
> /dev/sda1 ext4 / 9.31gb (1.5gb free)

> /dev/sda2 extended 109.93gb
	/dev/sda6 ext4 /home 95gb (15.4gb free)
	/dev/sda5 linux-swap 14.93gb

any ideas? solutions? 
how can I take more gb from swap, or should I take more gb from /home and leave swap as it is?

thank you

---

### Post by ibjsb4 on 2013-04-05
If thats your partition order:

You would have to resize sda5 to 11.93
Then extend sda6 to 98G
Then resize sda6 back to 95G
Then pass the 3G on to sda2
Then resize sda2 back to 106.93G
Then finally pass the 3G on to sda1

This is going to be one looooong process.  Without corruption? Should be ok, but one snafu and you are screwed.  I would not recommend it without backup.  Is that 3G worth it?

---

### Post by 007casper on 2013-04-06
you dont think it would be a smooth ride with gparted.  

I figured there is only 1.5gb left in the system section.  The system occasionally lags, or freezes.  I am bit worried that it might crash, or have performance issues due to space.  I have SSD drive.

I ran bleachbit as user
> 
The volume "home" has only 48.7 MB disk space remaining.

You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.

> 
The volume "Filesystem root" has only 0 bytes disk space remaining.

You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.

then, bleachbit as root
> 
The volume "Filesystem root" has only 107.3 MB disk space remaining.

You can free up disk space by removing unused programs or files, or by moving files to another disk or partition.

???

Then, I look at fileflight
It states /home is 93.5gb, and 15.4gb free; 
The filesystem is 9.2gb, and 1.5gb free

then, I look at it with Disk Usage Analyzer.
It states total filesystem capacity 110.4gb (used 88.1gb, available 22.3gb)

how come I am getting different information?

---

### Post by 007casper on 2013-04-06
bump

---

### Post by arpanaut on 2013-04-06
Your /home partition is just fine.
It is your / (root) system partition that is running out of space.
Do some cleanup on your system and remove some programs that you have installed that you don't use.
How many kernels do you have installed, check your /var/log files and see if anything there is extremely large.
If so then that could indicate that there is something wrong with your system.
Really with /home on a separate partition, a ~10 gig root file system should be adequate, so I would look into why it it so full.

---

