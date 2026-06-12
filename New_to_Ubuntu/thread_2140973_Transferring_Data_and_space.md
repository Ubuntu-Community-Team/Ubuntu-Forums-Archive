---
title: "Transferring Data and space"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by JonthueM on 2013-05-01
Is it possible to transfer one data from one partition to another along with the hard-drive space that it occupies? Like for example transferring 5 GB fold worth of music along with it the 5 GB space to which is occupy to the partition.

---

### Post by ibjsb4 on 2013-05-01
Not that I know of.  You would have to resize the partition(s) and move the data.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by sudodus on 2013-05-01
It is probably possible, but rather complicated and risky.

If you want to move your storage from one partition to another on the same drive, I suggest that you first copy the data (files) to another drive (for example an external drive). Basically, this will also give you a ***backup***. So if you extend the copying to all important data (documents, pictures etc), you get a backup, that might be valuable in the future (maybe in the near future).

When you have that backup, you can start editing your partition table. If you need to shrink one partition more than the its free space, remove the data you intend to move, shrink the partition and expand the neighboring partition to fill the unallocated space. These operations are done with ***gparted***.

Finally copy the data that you wanted to move to the expanded partition, and keep them on the backup drive.

---

### Post by JonthueM on 2013-05-01
Hmmm... I know when you shrink the partition past it limits files tend to be deleted. It would be really interesting and helpful to have it being done at the same time, where you just transfer files and the space it occupy and it automatically converts on the fly. Or have a map of files as well as the space they occupy and can just drag and drop to different partitions rather then shrink and then copy being unsure that those files have been sent to the black whole.

---

### Post by sudodus on 2013-05-01
The data is there, but the problem is the way to keep track of those data.

---

### Post by JonthueM on 2013-05-01
So when you shrink a partition like windows past its mark the files can be lost like lost track?

---

### Post by sudodus on 2013-05-01
A good partition editor would not let you shrink it below what is needed to contain the files that are there.

But if there is too little free space, there will be problems. Normally linux does not suffer from file fragmentation, but with too little free space, the situation changes.

---

### Post by Mopar1973Man on 2013-05-01
I'm like most of the people here I would rather use a DVD's RW's or some sort of large drive to move all data off the drive then partition it the way you want the drive then copy everything back. This way you always have a backup and your allowed to experiment with different ideas and layouts. Where playing the shell game it can become very challenging and dangerous for your data.

---

### Post by TheFu on 2013-05-01
> **Mopar1973Man said:**
> I'm like most of the people here I would rather use a DVD's RW's or some sort of large drive to move all data off the drive then partition it the way you want the drive then copy everything back. This way you always have a backup and your allowed to experiment with different ideas and layouts. Where playing the shell game it can become very challenging and dangerous for your data.

+1000
If you don't have a backup - **actually at least 2** - then your data is at risk already.  OTOH, if this is the case, then you probably can risk the data by just using gparted run from a liveCD and see what happens.  I wouldn't do this myself without excellent, multi-storage backups first, but that is just me.

If I read the OP correctly, which I'm not certain I did, it seems he wants to magically make storage move from 1 physical disk to another. I'd like that too. 

**My situation and solution:**
If fact, one of my backup storage areas needs to be relocated today from an internal disk to an external disk array. The external array doesn't have enough storage available, so I'm stuck.  What I'll end up doing is a multi-stepped process that doesn't risk the backup until after all the transfers are complete.
Steps:
* move the internal drive (/backups) to a USB2 connection, 
* pull another, smaller disk out of the external array to make room,
* add dual 2TB disks to the external array
* create a partition large enough to hold the backup area and other partitions for other uses. I'll probably use GPT, not MBR.
* setup the 2 new HDDs into a RAID1 set for the /backups area
* mount the new RAID1 storage to a temporary place on the server
* migrate over the data using rsync - could take a few days
* move the mount point from the USB2 UUID-based mount to the new RAID1 mount for /backups
* repurpose the old backup drive elsewhere; it is old, so it will not be used for anything critical.
* connect the removed, smaller HDD from the array as USB2 storage.

Notice how I don't touch the original copies of the data OR the backups during this process until the data is safely onto new storage?  That is by design.  I like this data and don't want to risk losing it.

OTOH, RAID1 for backups is overkill, so a fast, different solution would be preferred. Since this is for home use, not a business, a cheap USB3 external dock and a large, cheap, HDD will probably be deployed later for backups as the RAID1 storage fills up. RAID is not a backup.

Anyway, hopefully these steps will help someone else even if the OP can't use it.

---

### Post by n2kmaster on 2013-05-01
I'm having a similar issue, made my own distro of ubuntu, ran into an issue with the drive size for primary, installed a 40 gig drive, for some reason the clonezilla iso only gave me the first 15 gigs of the drive and I've been everywhere trying to find out how to resize the partition to its full size. I got GParted but it refuses to unlock the drive for me to resize the drive. Is there another method in fixing this? Did so much work here and without the space to use remastersys to get the distro off the machine im dreading having to start from scratch in making it all over again. The space left over on the 40 gig drive is not even partitioned as well. ANY suggestions would be appreciated.

---

### Post by Kopkins on 2013-05-01
It's always a good idea to have a backup if you are doing any sort of partitioning. I screwed up a partition once and lost 80GB of data.

---

### Post by n2kmaster on 2013-05-01
backups aren't my issue, trust me spent a good long time learning the difference between sda1 and sdb1. No my problem is the extra left over space that wasn't partitioned when i made a clone of the original drive. It limited a 40 gig drive to a 15 gig drive and didnt use the rest of the drive during the cloning process. Is there a way to extend that partition info to fill the entire drive instead of just the 15 gig cloned drive on that new drive?

---

### Post by sudodus on 2013-05-01
> **n2kmaster said:**
> backups aren't my issue, trust me spent a good long time learning the difference between sda1 and sdb1. No my problem is the extra left over space that wasn't partitioned when i made a clone of the original drive. It limited a 40 gig drive to a 15 gig drive and didnt use the rest of the drive during the cloning process. Is there a way to extend that partition info to fill the entire drive instead of just the 15 gig cloned drive on that new drive?

Yes :-)

But backup before doing any editing of partitions!

You can use ***gparted*** to edit partitions. If your partition is next to the unallocated space, you can expand the partition to use that space. 
```
gksudo gparted
```
Another alternative is to create a new partition to keep ***data*** from the system partition.

---

### Post by TheFu on 2013-05-01
To edit a partition table, the drive cannot be in-use. Boot off a LiveCD with gparted and go to town. It might be possible to edit non-in-use partitions on the boot drive without using a LiveCD, but I wouldn't. Call me paranoid.

---

### Post by n2kmaster on 2013-05-01
@TheFu - Thats exactly my plan of attack here, i have to get another copy of ubuntu, i used backtrack but modded it severely, but it registers as ubuntu 11.10. The original backups i can't even make a copy of them via iso or anything. Hence why i was cloning the hard drive to a bigger drive so i could make a iso backup of it. I'll leave this open so i can report back if i was successful doing this. I know someone else has to be pulling their hair out looking for an answer to it.

Gotta admit, the more i fiddle with Ubuntu, the more i like it.

---

### Post by sudodus on 2013-05-01
> **TheFu said:**
> To edit a partition table, the drive cannot be in-use. Boot off a LiveCD with gparted and go to town. It might be possible to edit non-in-use partitions on the boot drive without using a LiveCD, but I wouldn't. Call me paranoid.

+1
This is important (I should have mentioned to boot from another drive, for example the Ubuntu install drive). The only things I would edit with gparted on the same drive are labels.

---

### Post by JonthueM on 2013-05-01
Yes I would like the magical approach to moving data and the space its on to another partition (which would be a good idea for developing) but another reason is I don't have my 500 GB external drive  and I want to create a 3rd partition so i can access my files from both distro. I want to move every bit of my data  from the Ubuntu and windows partition to the  the third one. I know multiply cloud accounts is an option for backup but still would like another way to move data around hoping lol for a better solution.

---

### Post by TheFu on 2013-05-01
Why make a "clone"?  That is a Microsoft thing, and not needed for Linux. Any librsync backup tool works just fine - rsync, rdiff-backup, DejaDup, Duplicity, Duplicati, Back-in-Time ... there must be 200 others.

However, if you really want to clone an entire partition AND be efficient about it, use **partimage**.  It is smart about NTFS and ext2/3 partitions and will only clone the data, not all the empty storage too. Then it will compress everything.

I feel your love of Linux. It took me a few years, but times were very different back then.  Look for "boot repair" - it comes as either a program or an ISO - you want the ISO.  Then use yumi to put it onto a USB flash drive for easy booting.

Backtrack is not a normal Linux, IMHO. Wasn't it replaced by a distro with a different name recently?  I missed Outerz0ne (was out of the country), so I didn't see the new presentation on Kali ... that's the name - Kali.

---

### Post by n2kmaster on 2013-05-01
K heres why i have had to clone my drives. The original drive i installed, got updates on, modded, changed, installed programs on has like 800 megs space left on the hard drive. I'm trying to mirror the setup to another drive that unfortunately is on sata so im getting mild issues off the start. I have successfully wrote the grub, boot loader, etc all the fixings i need to get it up and running again and it worked via boot, problem is, the drive wasn't partitioned properly when i cloned it and it made a perfect mirror image of the 15 gig original ata hard drive. 

I've noticed that the drive has to be unlocked and the first thing that came to my mind and my googling was just that, use the ubuntu cd. I was seeing if there was another way of doing it. I was using Clonezilla to make the mirror image but i didnt see any settings to use the full drive instead of just making a mirror partition. 

Its a science experiment thats for sure :P Only thing im disappointed at is that i gotta get a new copy of ubuntu cuz i've beaten the tar out of my original copy and dog eared the corners of that book.

PS - Used backtrack simply for the airmon-ng section, i kept running into weird issues when i used a straight ubuntu 11.10 and it was to random of a problem to like "report".
[Sneaky peeky]("http://s15.postimg.org/4xkin89x7/Screenshot2.png") at what im working on. V1 is already on sourceforge. This already has been changed since this screenshot, colors fixed on the icons, more stuff setup on the 2nd bottom bar, etc. Trying to give everyone a Beini suite idea with some Anti-X, Lubuntu, Backtrack and original ubuntu feel to it while trying to keep a debian blue about it. Started as a home project, ended up being a distro project for everyone. Sorry for going off topic there. Will be reporting back how much of success the boot with CD is for me.

---

### Post by TheFu on 2013-05-01
Cloning the drives was the start of your issues, I'd guess.  In the last few years, the change from 512b sectors to 4K sectors has screwed with imaging software and screwed lots of end users.  OTOH, if you'd used a mirror tool and backups like rsync, rdiff-backup, etc .... to backup and restore across the optimally created file systems, only a tiny amount of wasted storage is likely before and after each partition.  Being aligned for new 4K sector disks impacts performance.  Let parted and gparted handle those things for you automatically.

Clonezilla - ah - never liked that tool.  Partimage is my choice, but only for MS-Windows, never for Linux. Cloning a Linux drive at the block level just seems like such a bad idea. I think you've learned 1 of the reasons why, but there are many others.  Having backups can be much more efficient than any clone solution and there are 20-500 reasons to have backups.  Clone=bad. Backups=good. I've probably beaten that point enough by now.

Create a list of the packages installed, backup the settings and data on the system and forget about backing up the OS crap.  It is best to reinstall anyway.  As long as you stay with software from repositories, you should be able to get back to the same place in about an hour.  Check out the dpkg --get-selections and --set-selections commands.

I don't understand how an old copy of Ubuntu can be worn out or how books wearing out is connected.  Bits do get old, but if the system can read them, it will work. ;)  Sorry, just missing the reference.

To mirror data between 2 drives, there are lots of ways.  From what you've described, seems like rsync would be perfect AFTER you build the new partitions and create new file systems in the way you like on the new HDD.  Then just mount the new storage into a temporary place and rsync. If files can change on the source, either boot into single-user mode or boot off a liveCD and rsync again.  The first time can happen on a running multiuser system. The 2nd rsync needs to happen on a quiesced system, but it will be 100x faster.

If you post the actual HDD devices of the system and the partition make up in a clear way here, perhaps an exact script will be provided to do what you need?  Text, not images, please.

---

