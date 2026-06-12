---
title: "Partitioning SDD + HDD"
date: 2015-06-05
forum: New to Ubuntu
---

### Post by Chris_Reeve on 2015-06-05
I am fairly new to Ubuntu and Linux in general. I have been doing a lot of research and reading as well as playing around with various distros in a VM. I think that I am just about ready to install, but I would like some feedback on my intended partitioning scheme.

I have a 256 GB SSD and a 1 TB HDD.

SSD:
/           30 GB
/home    whatever is left

HDD 1:
/var       10 GB
/tmp      20 GB
/data     whatever is left (will use this for backups of the SDD)
swap     16 GB

From what I have read, placing /var, /tmp, and swap on the HDD will help to reduce wear on the SSD (I am planning to set swappiness to 1 as my 8 GB of RAM should be sufficient). Do I really need to be concerned with SSD wear if I were to keep these partitions on the SSD? Will system speed be noticeably affected?

I plan on using UEFI, but have found inconclusive information on setting up the partitions on my SSD. This is what I am planning:
1. Use gparted to set the partiton table to gpt.
2. Perform the partitioning from the Ubuntu installer.
2.1. I do not need to create a /boot/efi partition as it will automatically be created (is this true when using manual partitioning?)
2.2. Which partitions should be primary and which logical (if any)?

I will mainly be using this computer for basic stuff, web browsing, email, etc. Also, I will be compiling android from time to time. I do not have much of a music/video/picture collection. I have much more space than I need.

Thoughts, advice?

---

### Post by Bucky Ball on 2015-06-05
Welcome. Just one comment. The /swap doesn't need to be anywhere near that big. 2Gb is fine. If you hibernate with LOTS of resources being used, same size as your installed RAM. Rarely necessary. 

Open a heap of apps, open a terminal, type 'top' and hit enter. Up the top there you should be able to see how much memory you're actually using.

Wear on modern SSDs is not what it once was. I wouldn't be too worried about it.

You are asking a couple of questions in the one thread here which can get confusing. You don't need to do anything to the SSD to install in UEFI, but you need to set the BIOS to make sure you are installing in UEFI. Ubuntu should do the rest, including creating the FAT32 UEFI partition. Yes, choose 'Something Else' at the partitioning section of install to partition manually.

Which partitions should be primary and logical??? Up to you. Hard to advise if we have no idea what partitions you need. In UEFI mode, doesn't matter how many of either you have. On a legacy install you are limited to four partitions per physical disk, regardless of if they're primary or extended partitions. Ubuntu will install to a logical partition inside an extended partition without issue. Windows will not.

NOTE: There are all sorts of myths and legends around about SSDs. Many stem from the early days when SSDs weren't as robust and were used with 25% (or more) free space to extend the life of the SSD. Well, you'll get all sorts of opinions, and some will be to ignore these things. I personally don't do much. I leave about 10% of the SSD free, but have plenty of room as I have three HDDs in that box. I also run the /swap on a HDD. /var and /tmp are on the SSD. 

The life expectancy of most SSDs now is up and people report them lasting as long and longer than HDDs.

That was a long 'one comment'! ;)

---

### Post by grahammechanical on 2015-06-05
> 2.2. Which partitions should be primary and which logical (if any)?

I do not think that is applicable if you will be using UEFI and GPT. It applies to BIOS and the partitioning table that comes with it.

> 2.1. I do not need to create a /boot/efi partition as it will  automatically be created (is this true when using manual partitioning?)

I think that you have to make a decision as to whether you will partition and then instruct the partitioner on which partitions to use and what for and you will have to do it for all system partitions. Or allow the installer to do everything automatically. I do not think that you can do a partial assigning of partitions and rely on the installer to do the rest.

Normally, the installer would put var & temp as folders under / in the / partition. You want var & temp to be on their own partitions. You will need to instruct the installer to do that. So, I think that you should also instruct the installer as to what partition should be the efi partition.

Regards.

---

### Post by Bucky Ball on 2015-06-05
You can move /var and /tmp later if you wish.

My mistake, yes, as mentioned by grahammechanical. You need to create the FAT32 partition (500mb is fine) during the 'Something Else' partitioning, but that is all. Ubuntu should 'automagically' use that for the EFI partition and install accordingly.

---

### Post by Chris_Reeve on 2015-06-05
Thank you both for your comments/advice. I am feeling more confident now.

---

### Post by Bucky Ball on 2015-06-05
All good. I generally advise a beverage of your choice, a pen and paper and a sit down to sketch out your partitioning plan prior to switching the computer on and partitioning, but you've already done that, so you're off to a good start. Slow and easy. Trying to figure out how you're going to partition the disk when you're sitting at the manual partitioning section of the install is not a good idea. ;)

Let us know how it goes and ask any more questions you need to. Good luck.

---

### Post by oldfred on 2015-06-05
Which drive is sda?
Grub defaults to sda and with UEFI it seems to only install to sda.  It overwrote my other Ubuntu grub in sda when I installed to sdb, even though I specified grub should be on sdb.

I like to have another / (root) partition or two and one one every drive. Just for testing or experimenting with settings or updates before changing my main working install.

I keep all system partitions on SSD and do not now worry about wear. Life of SSDs is comparable with hard drives, but even hard drives can fail relatively quickly.
 SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

And I have not fully partitioned either my SSD nor HDD. I did use large data partition on HDD and I keep /home inside / (root) on SSD. My new SSD is 128GB and I do not know what to do with all the space. I use 25GB for / with /home and have about half of that used. All data is on HDD. I plan on several additional / and create backup partitions on each drive. I have copy of /home on HDD and copy of some of the most critical data on SSD, but do not use a lot of space. Real backup is the copy of that data to DVD or flash drives.

---

### Post by Chris_Reeve on 2015-06-05
Everything went well and I have Ubuntu up and running! Having been a DOS and Windows user for 20+ years I am excited to learn something new!

---

### Post by Bucky Ball on 2015-06-06
Well done and excellent news. You learn fast. ;)

Please see the second link in my signature and mark the thread as solved. Please post new threads for any further issues/questions that may arise. Good luck and enjoy your new OS.

---

