---
title: "Problem installing Win7 Ultimate after installing Ubuntu 13.10."
date: 2013-11-12
forum: New to Ubuntu
---

### Post by kun.shandilya on 2013-11-12
I have a 320 GB harddisk which had 2 partitions previously-
200GB partition for Windows 7 x86 enterprise
90GB partition for Ubuntu 13.10 64bit

I decided to remove Windows 7, split the 200GB parition into two, 100GB each. I did so and installed windows 7 ultimate 64bit in one of them.

I had backed up all my data. _**ALL MY DATA**_ (which includes some _**REALLY IMPORTANT**_ stuff too) in my Ubuntu partition.
After installing Windows 7 I found that I couldn't use GRUB anymore (It is obvious, I know. I am new to Ubuntu) I tried the usual recovery methods but they didn't work. After booting from the LiveCD and running the fdisk -l command in the terminal, I found out that my UBUNTU PARTITION WAS MISSING!
Disk management of Windows 7 says that 93GB of Harddisk space is free.

My windows 7 install was a custom one but I am pretty sure that I had not tampered with the Ubuntu partition at all!
This is my boot-repair report. [www.paste.ubuntu.com/6404891]("http://www.paste.ubuntu.com/6404891")
Sorry if I sound too panicky but I really meant it when I said important data. 
:\

---

### Post by fantab on 2013-11-12
I am afraid but you seem to have somehow manged to format the Linux/Ubuntu Partition. Stop using your HDD immediately.
Boot with Ubuntu Live DVD/USB, as Live Ubuntu will NOT boot from HDD, so its safe for your DATA.

Install [**TESTDISK**]("http://www.cgsecurity.org/wiki/TestDisk"), see [this page]("http://www.cgsecurity.org/") as well, and try to recover your Lost partition if you can or recover your DATA. Be warned that 100% recovery may NOT be possible.

Good Luck...

---

### Post by kun.shandilya on 2013-11-13
TestDisk managed to retrieve my documents. Some applications aren't working after recovery but that wasn't a problem, I can download them again. Thankyou. One more question please, when I have to recreate the partition table, do I have to define the partition type (L,P,* and all that stuff) for ALL partitions or just the partition I want to recover? If so, can you please tell me what do I have to set for all the partitions?

---

### Post by fantab on 2013-11-13
That's good. I am glad that you were able to recover your DATA.

The following are your partitions from BootInfo Script:
```

parted -l:

Model: ATA ST3320813AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1048kB  105GB  105GB   extended
5      101GB   105GB  4292MB  logical   linux-swap(v1)
2      105GB   105GB  105MB   primary   ntfs            boot
3      105GB   210GB  105GB   primary   ntfs
4      210GB   320GB  110GB   primary   ntfs
```

Always have the First Partition as PRIMARY. You have instead an Extended Partition. If were you I would:
1.   100GB Primary NTFS Windows C:
2.   25GB Primary EXT4 Ubuntu /
3.   25GB Primary EXT4 Free [In case I want to install another distro or Ubuntu version or flavor]
4.   170GB Extended 
5.   166GB EXT4 Ubuntu /home [or no moupoint used; just a plain, simple Linux DATA partition]
6.   4GB SWAP

I suggest redo the partitions accordingly, using above guide, and re-install both Windows and Ubuntu. Partitions are Not something we do every few months. So getting them right is worth the effort. If you are re-installing Windows DON'T worry about 'boot' flag Windows will do it automatically. 
Just keep in mind, use only Windows tools to manage NTFS/Windows partitions and only Gparted/Linux tools to manage Linux/Ubuntu partitions.

---

### Post by kun.shandilya on 2013-11-13
Is there no way to create such a table without reinstalling? :\
And that extended partition used to be my Linux primary partition.

---

### Post by fantab on 2013-11-13
> **kun.shandilya said:**
> Is there no way to create such a table without reinstalling? :\


:D :D

You have only recently installed Windows and will have to install Ubuntu again...
Edit: Though Windows can boot from any partition other than first (XP won't), I always feel that it works best if it is on the First Partition.
The partition scheme I suggested is jut that, a suggestion. HDD Partitions are a very personal thing, only you know your needs best.

> And that extended partition used to be my Linux primary partition

That explains. It is possible that when you created three NTFS Primary Partitions and probably already had two primary partitions somehow the 4th Primary got converted to Extended. I am not sure if this has happened but....
Perhaps someone more knowledgeable might be able to shed more light on this.

---

### Post by Bucky Ball on 2013-11-13
Boot from a LiveCD, get to a desktop and launch Gparted. Your Ubuntu install will probably not have gone anywhere. Windows has no idea what a EXT partition is and will read it as free space, among other things. DO THAT BEFORE YOU DO ANYTHING ELSE. You should see your Ubuntu partition right where it was if you really didn't mess with it during Win install.

I have a feeling you are going on a wild goose chase for data that is not missing and you run the risk of really screwing it up.

When booted from the LiveCD I suggest you backup your data OFF the drive (an external drive or another drive in the same box and take it out) if it is that important. A good back up is generally not on the same drive as the original (if you simply moved your data to somewhere else on the same drive you have not backed it up at all).

---

### Post by kun.shandilya on 2013-11-13
Bucky ball - I got my data back already. :)

---

### Post by kun.shandilya on 2013-11-13
fantab - Yup that does. I got most of my data back without any error at all so I guess it was all still in the partition even though he partition was unreadable. Thanks a lot anyway :)
Recreating partition table won't delete my data, or will it?

---

