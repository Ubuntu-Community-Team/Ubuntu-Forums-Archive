---
title: "I cheesed the partitioning"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by lewdposter on 2016-03-24
thx

---

### Post by Bucky Ball on 2016-03-24
If you've only just installed, probably best to reinstall, but first, get a pen and paper and make a plan of how you are going to divide up your hard drive(s) before diving in.

If this install has been customised and a reinstall is not the preferred option, boot from the install disk, 'Try Ubuntu', launch Gparted once you're at the desktop and do some shrinking/expanding of the partitions, if  possible (i.e. you're going to need to shrink the partition next to / by 20-30Gb or whatever you need then expand / into the free space), to get it how you want it. 

Good luck.

---

### Post by grahammechanical on 2016-03-24
Ubuntu will not install in 100MB And Ubuntu installs into /. One of the first things the installer does is ask us to confirm that there is a minimum of, (I think) 6 - 8 GB. The recommended minimum is 5 GB. Even the server edition needs 1 GB.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Perhaps you are thinking of /boot? 

Regards.

---

### Post by oldfred on 2016-03-24
My suggestions on partitioning. But each user has his own requirements or different use of system, so adjust to your needs.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

 Oldfred's current partitions Dec 2015 for SSD & HDD with UEFI, note both drives not fully partitioned. Room for changes.
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by poorguy on 2016-03-24
Since this is about  partitioning is 40gb enough space for Ubuntu.

Not trying to high jack your thread.

Thanks.

---

### Post by oldfred on 2016-03-24
I normally install to a 25GB or so partition and use 11 to 13GB including /home of 2GB which includes .wine & Picasa.
But all my data is in a separate 200GB data partition and you may have little data or lots of data, so it is up to you. If you have all your data in /home and /home is part of / then you may want more.

I prefer in general to separate system partitions from data. Then reinstall is easier and backup of data only slightly easier.

---

### Post by poorguy on 2016-03-24
> **oldfred said:**
> I normally install to a 25GB or so partition and use 11 to 13GB including /home of 2GB which includes .wine & Picasa.
But all my data is in a separate 200GB data partition and you may have little data or lots of data, so it is up to you. If you have all your data in /home and /home is part of / then you may want more.

I prefer in general to separate system partitions from data. Then reinstall is easier and backup of data only slightly easier.


I just web surf / stream videos email / Google Earth a lot so yeah 40gb is plenty for what I do.

Thanks

---

### Post by lewdposter on 2016-03-24
From what I've read, this should work, much thanks for the answers.

---

### Post by Bucky Ball on 2016-03-24
Just wondering, and I may have missed it: is there a specific reason you are wanting a /boot partition or have you read somewhere you need one? You don't. Well, you don't need to manually create one in a BIOS install.

---

### Post by lewdposter on 2016-03-25
> **Bucky Ball said:**
> Just wondering, and I may have missed it: is there a specific reason you are wanting a /boot partition or have you read somewhere you need one? You don't. Well, you don't need to manually create one in a BIOS install.

Thank you

---

### Post by Bucky Ball on 2016-03-25
All good. At the most basic you only need to create / and /swap. Some go for a separate /home and some get more exotic and add /boot and other individual partitions for specific things (and reasons specific to the circumstances).

On a regular desktop install, / and /swap is all you really need. /boot partitions get full without proper housekeeping and eventually give 'no space left in /boot' errors when you try to update/upgrade. :)

(A caveat: a small EFI partition may also need to be created, but you may not even need to create that, depending on the existing setup and whether a clean install.)

---

