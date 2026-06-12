---
title: "Ubuntu Installation with 2 Drives"
date: 2016-09-02
forum: New to Ubuntu
---

### Post by shriggs on 2016-09-02
So after completing a new build, I'm ready to install Ubuntu for the first time. I have a 120GB SSD that I plan to use for booting and installing applications, as to utilize the speed of the SSD and improve my workflow. Then I have a 1TB HDD for other storage (documents, pictures, videos, etc.). So my understanding on how I can accomplish my goal is the following. I have an Ubuntu 16.04 image on a DVD. So I'll set that up and eventually get to the Installation type screen on the installer UI. Now, for the actual installation, I understand so far that the sda drive should be my SSD and the sdb should be my HDD. I should then create new partition tables for both, and add a new partition to sda, which will be my SSD. This will be for the root, so 102000 MB (102 GB, so 12% isn't used on the SSD cause I read somewhere that this is a good idea) in size, at the beginning of the space, an Ext4 journaling file system, and at the mount point "/" (for root). Now my first question is: should the "Type for the new partition" for this root partition be "Primary" or "Logical"? Alright, so then I understand that next I should add a SWAP partition, so a 16000 MB (I have a total of 16GB; but this is only rounded, so my next question is: do I need to have it exactly as the RAM [i.e. Ram of 16.24GB, so it has to be a 16240 MB partition]?) sized, located at the beginning of the space, and swap area used partition on the sdb device, or the HDD. Now which type of partition should this be, "Primary" or "Logical"? Finally, based on my knowledge right now, I understand that I should create one more partition, for /home. So I'm thinking this should be a 1008000 MB (which is, assuming the HDD is exactly 1024 GB total, 1024 - 16 GB, where the 16 GB is allocated for SWAP; and here, should I be calculating the absolute PRECISE size, even to the ones place in MB if I have to, or should I leave some space on the HDD like I did with the SSD?) sized, located at the beginning of the space, Ext4 journaling file system, and at the mount point "/home" partition on the HDD. And, again, you guessed it, should I choose "Primary" or "Logical" for the partition type? And then from there I'd click Install Now. Am I right on all this, to where it meets my goal of fast boot and program startup/loading, or am I forgetting something important? Also, do I need to add separate partitions for /boot, /tmp, /usr, /var, /srv, /opt, /usr/local, or any other mounting points/anything else at all? If so, how should I do so, how much space should I allocate, and where.
So, essentially, these are my questions:
1. Which type of partition should I choose when creating the root, swamp, and /home partitions ("Primary" or "Logical")?
2. Are all of the steps I outlined above, which are what I have gathered from research so far, correct in meeting my goal outlined at the beginning of this post, and somewhere in the middle of that paragraph up there?
3. Does the swap partition size have to be ABSOLUTELY PRECISELY the same as my total, to the nearest 0.001 GB, RAM?
4. Should I leave the 12% unused on the SSD (thus using 102/the total 120GB for the root partition)?
5. Should I use ABSOLUTELY PRECISELY every bit of data remaining allocated and free, not used by the swap partition, on the HDD, or should I leave some space unused like on the SSD? And if the latter, how much?
6. Do I need to add separate partitions for /boot, /tmp, /usr, /var, /srv, /opt, /usr/local, or any other mounting points/anything else at all and how much/where if so?
Whew, thank you very, very much if you read all that. And especially thanks in advance to anyone who can help clarify this information to me!

---

### Post by Impavidus on 2016-09-02
*1. Which type of partition should I choose when creating the root, swamp, and /home partitions ("Primary" or "Logical")?*

Ubuntu doesn't care. There are some rules: you can have at most 4 primary partitions on each drive, or 3 if you also have logical partitions, and there cannot be a primary partition between two logical partitions. But primary and logical partitions are a thing of MBR partitioning. The modern way to do things is using GPT partitioning, which has certain advantages.

*2. Are all of the steps I outlined above, which are what I have gathered from research so far, correct in meeting my goal outlined at the beginning of this post, and somewhere in the middle of that paragraph up there?*

Mostly correct, but I think that 102GB root partition is way more than you'll need. About 25GB will do. So you can use your SSD for some other things too. It's not entirely predictable which drive will be called sda and which sdb, but that doesn't matter, as the installer will set things up so that all system configurations refer to the partitions using UUIDs.

*3. Does the swap partition size have to be ABSOLUTELY PRECISELY the same as my total, to the nearest 0.001 GB, RAM?*

You write you have 16GB of ram. This usually means 16GiB=16×1024×1024×1024 bytes. 16GB hard drive space is 16×1000×1000×1000 bytes. So that's less. If you want to hibernate, the swap partition must be at least as big as ram, but it may be more. So you can round up. If you don't want to hibernate, there isn't really any reason to have more than 2GB of swap space.

*4. Should I leave the 12% unused on the SSD (thus using 102/the total 120GB for the root partition)?*

I'll leave that one to someone else.

*5. Should I use ABSOLUTELY PRECISELY every bit of data remaining allocated and free, not used by the swap partition, on the HDD, or should I leave some space unused like on the SSD? And if the latter, how much?*

I don't think keeping unallocated space on a HDD serves any purpose, except giving you more flexibility in case you want to change your partitions later, i.e., keep some space reserved for future use. And if you don't need all space on the drive, a smaller partition keeps the files a bit closer together, which may lead to a small speed-up. And in any case, you won't see the difference from leaving a few MB, or even a GB, unused.

*6. Do I need to add separate partitions for /boot, /tmp, /usr, /var, /srv, /opt, /usr/local, or any other mounting points/anything else at all and how much/where if so?*

You can make partitions for any directory you like (with a few exceptions that have to be on the root partition), but this will only be an advantage in very specific cases. So don't bother.

---

### Post by TheFu on 2016-09-02
Lots of opinions below. Some facts too.  

Update:  Impavidus's info is excellent. Only the swap size do we have different perspectives. Both are true and his probably reflects YOUR situation more than mine. ;)

For Linux-only systems, use GPT partitions, not MBR. It will make life much easier. That way, all partitions are primary and we aren't limited to just 4.

ext4 is the recommended file system unless you have specific needs which require another. It is a good default and I use it across all my systems.

For /, 25G is overkill.  100G would be .... er ... completely crazy. Linux isn't windows and you don't need that sort of storage for the OS and apps.

Swap - 4G is the recommended size, unless you will hibernate. With an SSD, why?  The old rules of 1-for-1 with RAM are extremely outdated.  On low RAM systems, 4G really helps as modern web browsers will easily suck up 2G of RAM alone. That is an issue for 2G RAM systems (like chromebooks).  

I'd put /home on the SSD too.  Start with 20G for that if a single-user system.

There is little reason to have more partitions than these days.
* /boot - only needed if LVM is used - ext2
* / - ext4
* /home - ext4
* swap - 4G unless hibernation is used. Then 1.0001x RAM size; it must 
* be slightly larger than RAM. Swap is there to let you "feel" the system   getting slower as RAM is used up.

In the old days, when storage was very tight, we had different file systems to prevent very important file systems from filling up. Unix doesn't like 100% full file systems. This was in the days of 20MB HDDs. Things are very, very different these days. Having a full HDD isn't very common and putting /home on a different partition basically prevents this from happening, plus it will make OS upgrades and backups easier.

If you use LVM, then there is much more flexibility with partitioning, but there is also greater complexity.  For someone very new to Linux, LVM is not usually recommended.

You didn't mention encryption. Was this on purpose? If encryption is used, LVM becomes smart and makes things much easier.  Do not choose to encrypt user's HOME directories. It causes slowdowns that are felt and other issues, like backups can't be automated without the user logged in.

My entire desktop is using 13G of total storage, btw. It also has 1.5G of RAM, since any more would be overkill for my needs. My chromebook (running a lite-Ubuntu), which gets used a bunch too, has 4G of RAM and a 4+G swap (slightly larger).  
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.8G        1.7G        346M        119M        1.7G        1.6G
Swap:          3.9G        202M        3.7G 
``` I have about 15 windows open on the chromebook, but most are terminals into other systems.
A "server" running here with 16G of RAM is using 1.4G of swap right now.  Just sayin'. Lots-o-swap just isn't necessary and would be a waste.

I would completely ignore the 2nd HDD for the install - actually, I'd unplug it during the install to be safer. Add it later and the storage is provides where it is needed.  Perhaps in a ~/Data/ directory under your HOME or just add it as /Data and use symbolic links from your HOME to the places that need extra storage available.  There are many reasons to do it this way.

Where is your backup storage? That is required.

Also, please break up paragraphs. That was VERY HARD to read.

---

### Post by shriggs on 2016-09-03
Okay, so follow up questions: 

1. How exactly do I do GPT partitioning?

2. Would having all mounting points, /, /home and /swap, being primary partitions work, with / still on the SSD and the other 2 on the HDD?

3. On my current Windows machine, with all my applications, Program Files takes up 67GB, Program Files (x86) takes up 24GB, ProgramData takes up 20GB, and AppData takes up 93GB. I understand that Ubuntu applications use up much less space than Windows, but, I mean, that's 200GB right there. I don't know if 25GB is enough, judging by that. Is it still?

4. If my SSD is actually sdb (which I'd judge by the size it shows on the installation partition manager UI thing), would I have to change the "Device for boot loader installation" to sdb?

5. I would like to assume that I'll hibernate at some point, as to be on the safe side. 16*1024*1024*1024 is ~17.1B, so 17.5GB should be good for swap? And would having this space allocated for swap, just in case, instead of just having 2GB, negatively affect my machine at all?

6. If I just allocate space for /, /home and /swap right now, can I create partitions for the other directories in the future, after installation, if the situation calls for it?

Now a little more directed towards TheFu's response:

1. If I do put /home on the SSD also, is there really a purpose for my HDD? And idk if even the 120GB is suitable for my storage. Unless personal files actually shrink in size in Ubuntu, like you and some others have mentioned apps do, I think I should keep /home on my HDD. Does having it on the SSD increase performance significantly though?

2. Where would using LVM be an advantage? I've heard of it, so idk if I will be using it.

3. By "[COLOR=#000000]Having a full HDD isn't very common and putting /home on a different partition basically prevents this from happening, plus it will make OS upgrades and backups easier[/COLOR]" are you implying that putting /home on the HDD is better? This seems to contradict what you wrote earlier.

3. Being fairly new to Linux, I didn't even know encryption was a thing. Is it really necessary where I am going to use Ubuntu for general use and generic, student programming (some app, game, intro web development, etc.)?

4. Again, fairly new to Linux, do you mean having an external hard drive for backup or another partition for that?

And, lastly, was this easier to read? :)

Thanks for the replies by both of you. They both gave me some great information and helped clarify things for me. I look forward to replies to these questions, and thanks in advance for them!

---

### Post by TheFu on 2016-09-03
This is gonna take 30min to reply.

> **shriggs said:**
> 
1. How exactly do I do GPT partitioning? gdisk, parted, gparted all support this. The disk will be wiped, since it sets up the basic formatting method. Do this before you start any install.

> **shriggs said:**
> 
2. Would having all mounting points, /, /home and /swap, being primary partitions work, with / still on the SSD and the other 2 on the HDD? Read up about GPT. There isn't anything other than primary partitions and it supports over 100 of them. No *effective* limits on the number or sizes of each partition. Plus the backup copy of the partition data is stored on the other end of the disk - much more reliable that way.

> **shriggs said:**
> 
3. On my current Windows machine, with all my applications, Program Files takes up 67GB, Program Files (x86) takes up 24GB, ProgramData takes up 20GB, and AppData takes up 93GB. I understand that Ubuntu applications use up much less space than Windows, but, I mean, that's 200GB right there. I don't know if 25GB is enough, judging by that. Is it still? Sounds like you game. Put games on a partition on the spinning disk. The programs just don't take that much on Linux.

> **shriggs said:**
> 
4. If my SSD is actually sdb (which I'd judge by the size it shows on the installation partition manager UI thing), would I have to change the "Device for boot loader installation" to sdb? Like I suggested, unplug the spinning disk before doing the installation.  During install the idea that sda or sdb won't be important and something called UUIDs will be used to mount the correct storage. UUIDs remove the confusion of sda/sdb/sdz ...

> **shriggs said:**
> 
5. I would like to assume that I'll hibernate at some point, as to be on the safe side. 16*1024*1024*1024 is ~17.1B, so 17.5GB should be good for swap? And would having this space allocated for swap, just in case, instead of just having 2GB, negatively affect my machine at all? Just wasted storage and swap that has to be managed by the OS.  I don't use hibernation on any of my machines and only use standby on 1 chromebook (running lite-ubuntu).  There are security considerations with hibernation which make it useless to me.

> **shriggs said:**
> 
6. If I just allocate space for /, /home and /swap right now, can I create partitions for the other directories in the future, after installation, if the situation calls for it? Sure. You can do anything.  Unix storage is really simple. If it looks like it is in the correct place, then it is correct.  For example, on a web server I run, I needed more storage under /var/www ... so I added another partition from another disk to the machine and mounted it to /var/www/ directly.  Then moved all the files from the old place over (not really those steps, but you get the idea).  You can mount a partition from any device where ever it is needed.  /home/thefu/games/extra/   - I can mount storage there, if it is needed. A "mount point" on Unix is just a directory. It should be empty, but if it isn't, that's fine too - all the files in it and below are inaccessible, however.

> **shriggs said:**
> 
Now a little more directed towards TheFu's response: I feel special. Thanks. ;)

> **shriggs said:**
> 
1. If I do put /home on the SSD also, is there really a purpose for my HDD? And idk if even the 120GB is suitable for my storage. Unless personal files actually shrink in size in Ubuntu, like you and some others have mentioned apps do, I think I should keep /home on my HDD. Does having it on the SSD increase performance significantly though?  SSDs are much faster than spinning disks. If you have the room, use all the storage on the SSD and keep HUGE data files on the spinning disk.  Things like mush, videos, game data, ISOs, backups ... put on the spinning disk.  If you run out of storage on the SSD, move the large files over.  You can use symbolic links to make storage appear to be mounted anywhere.

> **shriggs said:**
> 
2. Where would using LVM be an advantage? I've heard of it, so idk if I will be using it. If you don't already know, then you shouldn't use it at this point. It has some great advantages - think about dynamically sized partitions, grown and shrunk as needed and the ability to extend partitions across disks and storage types.  OTOH, using LVM improperly is how I lost 80% of my data back in 2002.  I don't extend file systems across different physical disks anymore without having 100%, great, know-I-can-restore, versioned, backups.

> **shriggs said:**
> 
3. By "[COLOR=#000000]Having a full HDD isn't very common and putting /home on a different partition basically prevents this from happening, plus it will make OS upgrades and backups easier[/COLOR]" are you implying that putting /home on the HDD is better? This seems to contradict what you wrote earlier.  Sorry - poor choice of terms.  "Full / partition" would have been a better way to say it. If you have a separate /home, then / will probably NOT get full without lots and lots of warnings - assuming you setup *alarming* on the machine. Since I run mainly servers, all my machines have alarming for common issues to be solved. This is not a beginner thing usually, but still I won't live without it.

> **shriggs said:**
> 
3. Being fairly new to Linux, I didn't even know encryption was a thing. Is it really necessary where I am going to use Ubuntu for general use and generic, student programming (some app, game, intro web development, etc.)? "Necessary" is a personal question.  There are many reasons for encryption.  For me, it is about having a failed disk and needing to send it in for a warranty replacement. I don't want those people having access to sensitive data I may have stored on the failed disk. If the disk stopped spinning, I can't scrub it before sending it back.  There are downsides to encryption too, but having good, solid, versioned, backups addresses those things completely. If you don't have proper backups, then encrypting anything is a really bad idea.

> **shriggs said:**
> 
4. Again, fairly new to Linux, do you mean having an external hard drive for backup or another partition for that? Backups need to be on a different physical disk or other storage media. That can be huge flash disks, spinning disks or network accessible storage anywhere you like. Just be certain to encrypt all backups that are on storage which isn't or might not be under your 100% complete control.


> **shriggs said:**
> And, lastly, was this easier to read? :)
 YES! Thank you!

> **shriggs said:**
> 
Thanks for the replies by both of you. They both gave me some great information and helped clarify things for me. I look forward to replies to these questions, and thanks in advance for them!  Helping people is fun on our side too. ;)

Don't be afraid to google for information and show that you have gotten some background data in your questions.  The wikipedia articles on GPT and LVM would be a great starting point.

---

