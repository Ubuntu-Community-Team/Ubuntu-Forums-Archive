---
title: "Ubuntu 12.04 and Win 7 Dual Boot Help"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by PerryThePerson on 2013-01-02
I have a 320GB HDD and I am about to do a clean install of Windows 7 and Ubuntu tomorrow. I have all my data backed up that I want to keep so losing anything on my hdd right now is not a problem.

I've read countless threads about this and I know this has been answered plenty of times, but what would be the best way to partition my HD so that everything will run smoothly.

I'll only have probably two or three games on my Win 7 partition, along with firefox, an antivirus, and probably nothing more than that. 

Any help will be much appreciated.

---

### Post by akshay.bhardwaj on 2013-01-02
Hi,

You can check details on this help page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope it helps! If you have any other query please feel free to ask.

---

### Post by oldfred on 2013-01-02
Welcome to the forums.

+1 on akshay.bhardwaj

I do not know how much space your Windows games may  take. Some seem to want a lot of room. The normal Windows minimum suggestion is 30GB, but then whatever additional your games may be.

If you want to share any data between Windows & Ubuntu I would also create a shared NTFS data partition. I always have had my Firefox & Thunderbird profiles in the shared data partition so I had same email & bookmarks in both systems. I prefer to separate operating system from data.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.


I might make the two NTFS partitions and then make the entire rest of the drive the extended partition with Ubuntu first & swap last. Then the space in the middle is /home and or data partition(s) or you might want an extra 25GB partition to install another Linux to test or test next version of Ubuntu.

---

### Post by rburkartjo on 2013-01-02
what i did was install ubuntu first then win7. worked great for me. after you install ubuntu use gparted to format your win7 part to 
ntfs. good luck

---

### Post by fantab on 2013-01-02
> **rburkartjo said:**
> what i did was install ubuntu first then win7. worked great for me. after you install ubuntu use gparted to format your win7 part to 
ntfs. good luck

I wouldn't recommend that to someone new to Linux/Ubuntu. 

[LIST]
[*]If we install Ubuntu and then WIN7 then Win bootloader will overwrite Grub and we will have to fix that...
[*]It is generally not a good idea to format Win install partitions with Gparted (not that it does not work). However Using Windows Disk Partitioning utility is a better and a safer option. Even if you have used Gparted to create a NTFS partition then reformat that Partition when installing Win7 using Win7.
[/LIST]
**PerryThePerson**, Install Win7 on the first Partition of the HDD formatted as NTFS Primary and about 50GB and another D: NTFS Primary about 20-50GB  depending on your need and you can use the rest of the HDD space for Ubuntu.


I have found that having a separate /ext4 Data Partition to store my data instead of /home more beneficial to me. I don't have to worry too much about losing/corrupting my Data during UPGRADES or Clean Installs.

---

### Post by maruf7 on 2013-01-03
Leave a partition (of proper space) for Ubuntu, First install Win 7, then install Ubuntu in the reserved partition.

---

### Post by audiomick on 2013-01-03
> **oldfred said:**
> ...if hibernating then you need swap equal to RAM [COLOR="Red"]in GiB not GB[/COLOR].

Thanks for that detail, Fred. That makes things clearer. I've been advising "a little larger than RAM" based on my own experience.

@Perry: I look at it this way: what difference does 3GB or so make on a 320GB drive really? If you are worrying about the last 3 or 4 GB, then it is time for a bigger or and additional drive. I set may swap space generously. It is unlikely to ever get used, but my hibernate works... ;)

Otherwise, +1 on a very good post from oldfred.

---

### Post by Aeonis on 2013-01-03
What if you already have 12.04?  I have my computer built now and put 12.04 on it and wanted to dual boot to Windows 7 for games.  I figure 50 GB on my 2nd hard drive will be plenty.  Would that work?

If so, how would one install Win 7 After 12.04 is installed?

Edit:  I just read it on that link from a previous post.  I don't fully understand how to fix the MBR from the LiveCD.  Does that mean boot into Ubuntu using the CD and then go into terminal and restore the MBR there?

---

### Post by oldfred on 2013-01-03
@   	Aeonis
If using a second hard drive probably best to disconnect Ubuntu drive and then leave Windows in first SATA port so it remains sda.
If not disconnecting be sure to set Windows drive as boot drive in BIOS before install as that is where Windows will install its boot loader.
If more questions best to start your own thread to avoid confusion on who is responding to what question.

---

### Post by PerryThePerson on 2013-01-04
After spending the day reinstalling Windows, Drivers, Ubuntu, Updates everything is up and running smoothly. Thank you to everyone who helped with this. I've gained a little bit more knowledge with partition so that'll help for future things I'm sure.

---

