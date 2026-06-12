---
title: "How to use an unallocated space?"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by Grigoriy on 2017-07-05
Hello!
                          I've got about 65GB of an unallocated space in  Ubuntu Desktop 14.04 and I have no idea how to use it. When I try to  make a new partition, it says that there could be only 4 primary ones.

---

### Post by Bucky Ball on 2017-07-06
And you have four. sda5 is within the extended partition sda3 so is not counted as one of the four. You have a legacy install which limits you to four partitions. One way around this is to delete sda4, a primary partition, and expand sda3, the extended partition, to include the rest of the unallocated space. You can then create another partition inside the extended partition or another primary.

Another way would be to resize sda4 somehow. To resize partition they must be unmounted. Goes without saying, but I will, that you should backup anything you don't want to lose just in case.

Also, I have no idea how you would have Ubuntu anything installed on that computer as they are all NTFS partitions. Ubuntu will not live on one. Where have you got Ubuntu 14.04 installed? Are you using WUBI, Ubuntu installed inside Windows?

---

### Post by Grigoriy on 2017-07-06
Thanks for your reply! No I won't start deleting anything, unless I know what exactly am I doing and what would be consequences of it.
I'd rather lose that 60 GB of free space. It's only about 10% of all the space I have on 2 physical HD's. Especially when I have a dual-boot system with GRUB2 sitting God knows where. I don't want to end up with a dead system where I have to waste another couple of days to get stuff back in order. Ubuntu is sitting on another physical HD, which is connected via USB3 that connects dock station with Ubuntu disk (sdb) and my notebook with Windows inside of it (sda). So it's very simple.

---

### Post by Bucky Ball on 2017-07-06
In that case, I suggest you boot into Windows and do this there. You are working via Ubuntu on sdb on a drive that is Windows only with a Windows OS on it and its associated partitions. You do not want to start screwing with that with Linux partitioning tools. I suspect sda4 is some kind of Win recovery partition so removing or resizing that would indeed be disastrous.

You won't get much information looking at this via Gparted. Boot into Windows and you will get more accurate information pertinent to the OS that is installed on that drive.

---

### Post by Grigoriy on 2017-07-06
You're funny - first you said "One way around this is to delete sda4..." And then you said "I suspect sda4 is some kind of Win recovery partition so removing or resizing that would indeed be disastrous."
That's why I said that it's best not to do anything, than to do nothing (especially when it can damage stuff).

---

### Post by Grigoriy on 2017-07-06
For those who care to know... I used Paragon Hard Disk Manager from within Windows 7 environment to  find out that it was actually a Windows recovery partition. It appeared  as WinRE. I read online that I could safely delete it. So I used GParted  in Ubuntu to get rid of it and then  I made bigger my extended partition sda3, made bigger my NTFS partition  sda5 and created a new logical partition EXT4 (used ext4 fs for that).  So not only I reclaimed my 65 GB of a free space, I was also able to  create ext4 partition. And that ext4 partition is important because I  use it as a temporary storage medium when I do Ubuntu backups (I save  them on ext4 partition and not on ntfs one). Both OS seem to work fine.

---

### Post by Bucky Ball on 2017-07-06
> **Grigoriy said:**
> You're funny - first you said "One way around this is to delete sda4..." 

Nothing funny about it. Once you revealed that this is a Windows disk you are working on while trying to use Ubuntu from another disk to do it, all bets are off. 

Provide as much information as you can to start, get accurate support. Good luck and glad you've found it amusing. As such, won't waste any more of your time or mine here. 

If you've solved your problem, please mark the thread as solved to help others.

---

### Post by Grigoriy on 2017-07-06
I don't have to "reveal" something that is obvious. All my partitions **on my 1st image **were NTFS. Did you see any Linux partitions there? Then, that would mean - it's a Windows disk. Also you could see a LABEL "**W10**". What else that could stand for if not for Windows 10? No need to advise before you even know yourself what the question is. If you're unsure - just ask. It's the same if someone asks you in a street - how do I get to the train station (that person doesn't know you've got two of them in your own town). Then it's your job to ask that stranger which station he needs to get to. And not to send him to one which he might not even need. Simple logic. Sometimes people don't know what must be revealed. Because when you write too much in your first post, no one would read it.

---

### Post by Topsiho on 2017-07-08
I back Bucky Ball here that incorrect information leads to "funny" advise. Bucky Ball is a highly estimated and very active member of this forum, who generally gives good advise. And doesn't need to be snubbed at by someone seeking advise and who gives incorrect information. Nowhere in the first post of the original poster is mentioned that he has 2 hard disks, and the disk that he shows has only NTFS partitions.
So ...

Topsiho

---

### Post by wildmanne39 on 2017-07-08
Let's stay on topic please and remember the CoC:
> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.
Everyone makes mistakes from time to time or does not see information posted even in a screenshot.

Thanks

---

