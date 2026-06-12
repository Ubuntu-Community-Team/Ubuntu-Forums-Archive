---
title: "Prolonging life of SSD by not using the Home partition?"
date: 2014-09-25
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-25
On Windows, it is recommended that the system files be on the C drive (and the C drive should be on the SSD) and all other files (such as documents, media files, and music) be on the D drive (and the D drive should not be on the SSD as you constantly write and delete data on this partition).

What is Linux's equivalent way of dealing with this? I am new to Ubuntu and from what it seems like, the root partition contains all system files (like the C drive) and the home partition contains everything else (like the D drive), BUT also includes cache and some config files from applications of the C drive. Should I treat both the Root partition and Home partition as the "C drive"? if I do so, then I'm guessing the Home partition can be shrunk down to like 2 GB if all it contains is cache and config files (what other files besides these that are system-related?). And then another partition should be created to store all my personal files unrelated to the functionality of the installed applications. 

Thanks.

P.S. I read that ext4 only defragments when the partition exceeds 80% of usage, otherwise files are intelligently placed on the drive with spaces between each file that takes up the file to allow the file to grow in size without affecting fragmentation (something like that). I also read that it will automatically move files that exceed this growth in size to deal with fragmentation. What would need to be done (if anything) about this for an SSD? I'm just asking this out of curiosity because I will be storing large media files on a HDD anyway, not SSD.

---

### Post by Michael_McKenney on 2014-09-25
SSD drives will degrade over time.  You could install your OS on a SATA drive and only data on the SSDs.  You get 20,000-30,000 r/w IOs per sector on most SSD drive before they close that sector and move it to the next available sector.  My friends have tried and removed SSD drives from CAD and A/V workstations and servers because of it.  Heavy storage IOs will degrade the SSD over time.  If you are worried about it, don't use SSDs.  I use SAS drives and SAS RAID at home because my workstation projects require heavy IO usage.  It was expensive but the drives were designed for it.  SATA and SSD drives are not.   I would not worry about defragging the drive as your main problem.  Temp and Paging files can kill a drive faster.  They constantly write to those locations.

---

### Post by Impavidus on 2014-09-25
Think about how much 20,000 writes actually is. Suppose you replace all files on a /home partition filling the entire SSD every day. This gives you one write every day on each sector of the SSD. With 20,000 writes available it should hold for about 50 years. But you don't replace your entire music collection every day. Or consider log files. They are written thousands of times per day, but they are small, so only a single sector of the SSD is involved each time. With some clever caching multiple entries to the log can be made in a single write. With millions of sectors available and the SSD cleverly moving sectors around using its wear levelling algorithm, of which the OS is completely unaware, it will take millennia before log files have been written 20,000 times to each sector.

In most cases the amount of storage you get for the money you spend is more important than wear of the SSD. If you want to store terabytes, spinning disks are cheaper. But there are some things that you don't want to write to an SSD, like large caches, large temporary files or swap (which you want to avoid anyway).

As to moving files to prevent fragmentation, I don't know. Although I imagine that the system can instruct the drive to copy the contents of sector A to sector B and discard the contents of A, which an SSD can do by relabelling the sectors without actually moving data around.

---

### Post by kira-yamato-2008 on 2014-09-25
While Michael_McKenny is correct on the above, he left out something very important. Do not **EVER** use an SSD for swap space. Also SCSI devices can be temperamental, and require a low noise environment to prevent off track writing. For a SSD I'd only really put things that are pretty static on it. One reason is because of how often root things are updated, and how often that requires removal of old stuff, especially when there's an upgrade.

---

### Post by Michael_McKenney on 2014-09-25
I have been using SCSI and SAS drives for 20+ years.  Failure rate is very low.  Noise problems are only in factories.  Office and home environments don't get RF noise from machinery.  In Windows, temp and paging files are not recommended on SSD or RAID 5 or above.   I would guess the same with /tmp and /swap in Linux.  SATA for your OS and SSD for apps/data.  If you are doing CAD or A/V work, I would not use SSD.   SSD don't like heavy IOs from CAD of A/V apps.  

SCSI requires better cooling and power supplies.  SATA is basically SCSI interface with EIDE disk technology.  SAS/SCSI holds 256 instructions on the PCB and has much less disk density to maintain performance and reliability.   SAS/SCSI can go 600 to 900 GB per drive.  SATA 2-4 TB.   Problem with SATA is vibration on a high density platter can cause issues.  Drives are packed tighter and not cooled properly.  

My SAS RAID and 15K drives are faster and better than SSD drives.

---

### Post by garycheng12 on 2014-09-25
> **Impavidus said:**
> . But there are some things that you don't want to write to an SSD, like large caches, large temporary files or swap (which you want to avoid anyway).


I'm guessing ideally I would want caches, temp files, and swap (not just large ones, but small ones as well for the sake of having these types of files in one place) in the home partition. I'm also guessing that I would likely encounter problems because some applications may not provide me the option to re-direct the cache folder from the root partition to the home partition (for example, cache is is so "behind-the-scenes" of a program that users should never have to touch it... if there are any).

Also, let's say I'm not using any SSD but I want all system files (and cache, config files, what-not that that would be on a Home partition) on the root partition. I would have to not create the specific Home partition and instead create a regular, untitled partition so that programs will know not to use the secondary partition to store these files that would otherwise be on the Home partition? 

I'm asking because I've read that even though the option is available to upgrade a distro every 6 months, it is still highly recommended to completely install the distro from scratch. I'm not sure if any cache/config files/other miscellaneous system files that could be on the Home partition which is not reformatted would interfere with the root partition that is to be reformatted for the upgraded distro.

---

### Post by kira-yamato-2008 on 2014-09-25
> **garycheng12 said:**
> I'm guessing ideally I would want caches, temp files, and swap (not just large ones, but small ones as well for the sake of having these types of files in one place) in the home partition. I'm also guessing that I would likely encounter problems because some applications may not provide me the option to re-direct the cache folder from the root partition to the home partition (for example, cache is is so "behind-the-scenes" of a program that users should never have to touch it... if there are any).

Also, let's say I'm not using any SSD but I want all system files (and cache, config files, what-not that that would be on a Home partition) on the root partition. I would have to not create the specific Home partition and instead create a regular, untitled partition so that programs will know not to use the secondary partition to store these files that would otherwise be on the Home partition? 

I'm asking because I've read that even though the option is available to upgrade a distro every 6 months, it is still highly recommended to completely install the distro from scratch. I'm not sure if any cache/config files/other miscellaneous system files that could be on the Home partition which is not reformatted would interfere with the root partition that is to be reformatted for the upgraded distro.

The simplest solution might be for you to keep a secondary data partition for all of your personal files. While keeping all system relevant information, such as the entire OS and installed programs, on the primary partition. The best way to do that is to have personal files on a separate hard drive all together, and in optimal conditions in several other places, across a variety of storage mediums.

When you go to reinstall the OS fresh with a freshly formatted partition you should assume that your previous programs won't work on the upgrade and fresh installation. Thus you should reinstall your apps purely for the sake of it being an entirely fresh install of the OS, therefore all personal data such as: Bookmarks, photos/other images, documents, videos, audio files, and any other files you can't replace, or would be inconvenient to download again for what ever reason... Should be stored separately, in multiple places, and on at least two different storage mediums.  

In which case you'd install the OS and your Applications on to the SSD, then put everything else on a traditonal HDD, with redundant copies on say DVD RWs/BluRay REs, external HDDs, cloud storage, and/or etc. 

> **Michael_McKenney said:**
> I have been using SCSI and SAS drives for 20+ years.  Failure rate is very low.  Noise problems are only in factories.  Office and home environments don't get RF noise from machinery.  In Windows, temp and paging files are not recommended on SSD or RAID 5 or above.   I would guess the same with /tmp and /swap in Linux.  SATA for your OS and SSD for apps/data.  If you are doing CAD or A/V work, I would not use SSD.   SSD don't like heavy IOs from CAD of A/V apps.  

SCSI requires better cooling and power supplies.  SATA is basically SCSI interface with EIDE disk technology.  SAS/SCSI holds 256 instructions on the PCB and has much less disk density to maintain performance and reliability.   SAS/SCSI can go 600 to 900 GB per drive.  SATA 2-4 TB.   Problem with SATA is vibration on a high density platter can cause issues.  Drives are packed tighter and not cooled properly.  

My SAS RAID and 15K drives are faster and better than SSD drives.

My statement was for actual sound noise, not RF interference. Also why I avoid really high density drives, because they're rather even worse. If I shout at a 2+ TB drive I can literally see dramatic slowdowns in it's read/write times. While SCSI failure rates are rather low, they can still be temperamental, and costly for home uses. For CAD, A/V, Servers, and other high demand tasks they're fantastic, but impractical for standard home, and regular business uses. 

Then again I rarely worry about EIDE disk bases, because I have SpinRite, and drive failure other than serious hardware failures in the drive it self are easily corrected with SpinRite. 

I digress though this is off topic. What the OP originally wanted to know was how to extend the life of his SSD. The easiest way to ensure that is to place the OS on it, and other relatively permanent files on it. For example; games, word processing, image editing, and other applications you intend to keep for long periods of time, and still want to load quickly.

---

### Post by Michael_McKenney on 2014-09-25
My SAS drives are not that loud compared to my 6970 video adapter fans.  I reduced chassis noise with Panflo fans.  My workstation is on when I am watching TV and it does not bother me.  

Spinrite brings back memories.  I remember Debug g:c800 on my MFM drives in the 80s.  Most I know use SATA for OS and SSD for games and apps only.

---

### Post by snowmobiler on 2014-09-25
Just a quick question to add as part of the swap discussion. I am new to Ubuntu so all I did on my pc and laptop was install using the entire drive for root and home. However Ubuntu automatically creates a swap space. I think it makes it equal to the amount of RAM you have installed. So how do you avoid that? Do you choose the "something else option" instead of the first option which is use the whole drive. Then DONT create a swap partition? Or would Ubuntu still create one if you didn't? I ask as I have been inquiring into the pros and cons of SSDs and that was the first i saw of DONT put a swap space on the SSD.

---

### Post by Tadaen_Sylvermane on 2014-09-26
It should be noted to people afraid of killing their ssds... they last for decades under normal use. [http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb) . It is really not an issue to be concerned with. The drive is more likely to die from a controller failure than you run out of writes, swap included.

---

### Post by mastablasta on 2014-09-26
> **snowmobiler said:**
> Just a quick question to add as part of the swap discussion. I am new to Ubuntu so all I did on my pc and laptop was install using the entire drive for root and home. However Ubuntu automatically creates a swap space. I think it makes it equal to the amount of RAM you have installed. So how do you avoid that? Do you choose the "something else option" instead of the first option which is use the whole drive. Then DONT create a swap partition? Or would Ubuntu still create one if you didn't? I ask as I have been inquiring into the pros and cons of SSDs and that was the first i saw of DONT put a swap space on the SSD.

yes, that is how you do it. and with enough ram you can reduce the usage of swap to minimum. or you create swap on your HDD.


> **garycheng12 said:**
> I'm guessing ideally I would want caches, temp files, and swap (not just large ones, but small ones as well for the sake of having these types of files in one place) in the home partition. I'm also guessing that I would likely encounter problems because some applications may not provide me the option to re-direct the cache folder from the root partition to the home partition (for example, cache is is so "behind-the-scenes" of a program that users should never have to touch it... if there are any).

Also, let's say I'm not using any SSD but I want all system files (and cache, config files, what-not that that would be on a Home partition) on the root partition. I would have to not create the specific Home partition and instead create a regular, untitled partition so that programs will know not to use the secondary partition to store these files that would otherwise be on the Home partition? 

I'm asking because I've read that even though the option is available to upgrade a distro every 6 months, it is still highly recommended to completely install the distro from scratch. I'm not sure if any cache/config files/other miscellaneous system files that could be on the Home partition which is not reformatted would interfere with the root partition that is to be reformatted for the upgraded distro.

I would say leave the home on root (/), move /var and /swap on HDD.


> **Tadaen_Sylvermane said:**
> It should be noted to people afraid of killing their ssds... they last for decades under normal use. [http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb) . It is really not an issue to be concerned with. The drive is more likely to die from a controller failure than you run out of writes, swap included.

does this go the same for USB stick? or are clash drives completely different? as I know they now too have low level wear algorythms. 

I plan to use the stick for now and replace it with small SSD later when I have the money for it.

---

### Post by Michael_McKenney on 2014-09-26
I hear of SSD crashes monthly from my friends.  I am wondering if it is heat causing it.  I can't see them getting past the limits.  In my workstation chassis I had the power supply customed wired by PC Power and Cooling.  The SAS cables don't block air flow.  I made sure the front fans have available space over the drives.

---

