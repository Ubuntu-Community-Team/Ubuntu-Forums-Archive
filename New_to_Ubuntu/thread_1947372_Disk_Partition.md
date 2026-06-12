---
title: "Disk Partition"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by CoDeHacKer on 2012-03-26
Hi, I am wanting to try out a few different distros, I have a 160GB External HDD
in a USB 3.0 enclosure. I had set it up in 20 GB partitions with 3 primary and 1 
extended partition with logical drives. I had planned on putting a couple of versions
of windows on 2 of the primary partitions, and Ubuntu on the 3rd, then installing 
several different versions on the rest, just to try them out to see what I liked best.
 
I was able to make the live CD ok, and it boots up fine, but now I am seeing and 
reading that I need 3 partitions for Ubuntu. As far as I can understand I should have 
one partition for /boot one for /home and one, which it is best if it is on a extended 
partition, for /swap. 
 
I had set up a 8MB partition at the beginning of the drive and formatted it ext 4 and 
labled it /boot I wonder is that enough space ? I read 8MB, then after more reading 
I read 100 MB, so I was wondering what is best for /boot, and after reading here, 
I"m confused if it should be /boot or just / at the first partition. Then I am seeing /user
/svr /var /tmp and all of that.
 
My question is, exactly how many partitions do I need to install Ubuntu, and what 
should they be labled, and what is the min/max space required for each, and what
should they be named, and which ones should be in the primary partitions, and which
in the extended partition.
 
I was also curious if the /swap file can be shared by different distros of linux.
 
I don't want to allocate too much space, but I don't want to be running out of space 
either, and I want to be able to sleep/hibernate. 
 
I have searched around, and have been unable to find any documentation on this, 
if there is some documentation somewhere, that would be nice too.
 
Thanks

---

### Post by sandyd on 2012-03-26
> **CoDeHacKer said:**
> Hi, I am wanting to try out a few different distros, I have a 160GB External HDD
in a USB 3.0 enclosure. I had set it up in 20 GB partitions with 3 primary and 1 
extended partition with logical drives. I had planned on putting a couple of versions
of windows on 2 of the primary partitions, and Ubuntu on the 3rd, then installing 
several different versions on the rest, just to try them out to see what I liked best.
 
I was able to make the live CD ok, and it boots up fine, but now I am seeing and 
reading that I need 3 partitions for Ubuntu. As far as I can understand I should have 
one partition for /boot one for /home and one, which it is best if it is on a extended 
partition, for /swap. 
 
I had set up a 8MB partition at the beginning of the drive and formatted it ext 4 and 
labled it /boot I wonder is that enough space ? I read 8MB, then after more reading 
I read 100 MB, so I was wondering what is best for /boot, and after reading here, 
I"m confused if it should be /boot or just / at the first partition. Then I am seeing /user
/svr /var /tmp and all of that.
 
My question is, exactly how many partitions do I need to install Ubuntu, and what 
should they be labled, and what is the min/max space required for each, and what
should they be named, and which ones should be in the primary partitions, and which
in the extended partition.
 
I was also curious if the /swap file can be shared by different distros of linux.
 
I don't want to allocate too much space, but I don't want to be running out of space 
either, and I want to be able to sleep/hibernate. 
 
I have searched around, and have been unable to find any documentation on this, 
if there is some documentation somewhere, that would be nice too.
 
Thanks
The minimum number of partitions is 2.
One is the root (/) and one is the swap.

The root is where everything goes (i.e. documents, apps , etc), and swap is the same thing as a windows paging file. If you want to enable hibernation, you will have to have a swap space the same size or larger than your RAM.

You can also have three partitions (one root (/), one home(/home), and one swap).
Your home partition is where all your personal settings, documents, desktop, and anything else that is uniquely yours is stored. Some people have a seperate home partition so that if Ubuntu dies, or they want to do a clean install instead of an upgrade to the next version, they can reinstall Ubuntu without deleting all their data.

Normally, /home resides in / (root)

---

### Post by cortman on 2012-03-26
Since you can only have 4 primary partitions on the HD, I would recommend creating 3 primary partitions (for OS's) and then an Extended partition, within which you can create an unlimited number of logical partitions. Use the logical partitions for swap. You can use them for data and to install OS's on as well.

---

### Post by nazar91 on 2012-03-26
Sometimes /boot is seperated because of security reasons. Being always mounted it has greater chance to be damaged. If you want to do so 100 mb is more than enough. Also some very old BIOS could not boot / more than 8,5 Gb. 
Is recomended (by some distribution) to seperate /home partition. After reinstallation your data and settings wil be saved. Usually it's the biggest one.
/var partition is usually seperated on web, ftp and some others servers (even on another hard drive) because of intensive reading/writing in /var directory.
/tmp is usully seperated on file servers for best file exchanging experience. 
swap can be used by others, but not simultaneously.

---

### Post by jerome1232 on 2012-03-26
For a regular user, I would just go with a big fat /, it can be on a basic or logical partition, swap also can be on a basic or logical.


For the most part only servers need to separate out many of the partitions in an advanced layout.

---

### Post by sandyd on 2012-03-26
> **cortman said:**
> Since you can only have 4 primary partitions on the HD, I would recommend creating 3 primary partitions (for OS's) and then an Extended partition, within which you can create an unlimited number of logical partitions. Use the logical partitions for swap. You can use them for data and to install OS's on as well.
This is why you use GUID.

---

### Post by CoDeHacKer on 2012-03-26
Thanks for all the advice, 
 
After I posted I found this guide, I've been searching for a while now. It must be older, because I have like 8gigs of memory. 
 
[http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html)
 
I'm trying to fix it so grub is in the first 8mb sector, and that the first sector is so small 
that Windows will not even try to overwrite it, and then install Ubuntu in the first 20 
gig part /, then use a 20 gb swap in one of the logical drives near the center of the 
drive, it's almost 3x my memory, then use a extra /home for well /home, and have a 
fat32 logical partition of 20MB so windows or linux can read from it and save stuff 
there.
 
I guess that will work, I just don't want to have to redo it 20 times. I'm just 
playing for now, and trying to fix something up so I can boot any machine
from the external drive.
 
Thanks again

---

### Post by oldfred on 2012-03-26
Your link is very old. Now you just have to have for most desktops / (root) and swap. If booting several distros you may want a shared data partition so you can access the data easily from all systems. 

Do not use FAT anymore, but use NTFS. FAT does not have a journal and cannot save a file over 4GB.

If data or /home is separate you only need 10 to 25GB for / (root). I like to have some extra so if I write a backup 4GB DVD my /tmp in root is not filled.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

With an external drive you have to use manual install to get the option on where to install the grub2 boot loader. You want it in the MBR of the external drive. If installing multiple systems you have to decide which will be the one you want to be your primary system and keep it in the MBR.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

