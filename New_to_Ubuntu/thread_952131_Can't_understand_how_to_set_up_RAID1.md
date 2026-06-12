---
title: "Can't understand how to set up RAID1"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by octotracy on 2008-10-18
Hi,

I've been trying to figure this out myself, but now I'm more confused than ever.

I have xp and hardy set up dual boot on 1 hdd.  I also have 2 500gb drives that I would like to set up in RAID 1 for data.  All the tutorials I've found are for setting up raid for the OS and the mdadm manual was complete gibberish to me :(  I haven't used the terminal much and have only pasted into before.  Can't seem to figures out how to write commands correctly.

Can anyone help with this?  Alternatively, does anyone know the best way to have my data on the 2 drives so that it's backed up?  I know I could  (somehow) set it up so that I copied the data from one to the other regularly, but how would I do this so that it only copied new stuff?

Hope this makes sense and that someone can help.  Much appreciated

---

### Post by b0b138 on 2008-10-18
do you want to access the raid array from both xp and ubuntu?

---

### Post by nhasian on 2008-10-18
first i just want to verify, your motherboard doesnt already support raid arrays?  If so you can just create the raid array from the motherboard's bios and it will just be seen as a single drive by the OS.  This is the preferred method I think unless you have a dedicated raid adaptor which is the fastest :)

anyway, this guide can help you set up software raid in ubuntu 8.04 hardy heron:

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

---

### Post by octotracy on 2008-10-19
My flatmate's managed to set up the mirror using mdadm.  But we can't get the array formatted and therefore can't mount it.  We've used gparted to try to format it and it just says

create new fat32 filesystem
>mkdosfs -F32-v /dev/mdop1
 >mkdosfs 2.11 (12 Mar 2005)
 >/dev/md0p1: No such file or directory

We're formatting it as Fat32 so that windows can hopefully see it. I can see the array in Computer but it isn't mounted.  Any ideas?

---

### Post by nhasian on 2008-10-19
okay here's the part thats bothering me...

if your running software raid in linux, then linux would have to be running in order to use it.  obviously if you just want to access the data on the raid array over a network connection than you can use any filesystem you want FAT32, NTFS, EXT3, etc, but if you want to access it in windows from your local machine (dual booting) you are going to have problems.  

your not going to see the raid array in windows since it wont be running.  you may see the two individual drives with identical data since your mirroring them.  but what happens when you modify data on one drive and boot back to linux?

What make/model of motherboard do you have?  most modern motherboards have some type of raid built in.  worst case scenario is you'd have to buy a cheap raid adaptor to do hardware raid.  that would resolve your problem and allow you to use the raid array with multiple operating systems.

> **octotracy said:**
> We're formatting it as Fat32 so that windows can hopefully see it. I can see the array in Computer but it isn't mounted.  Any ideas?

---

### Post by Kellemora on 2008-10-19
Hi OT

I'm just chiming in to ask WHY you would want to use RAID at all, unless it was at minimum a RAID 5 system ?????

RAID 0 and RAID 1 are NOT what they are tauted to be!

Your data is no safer and could actually get mangled easier than using simple hard drives.
If you're after speed, buy faster hard drives.
But I can tell you up front, there is not much difference between 7200 and 15000 speed drives, except the 7200 will last longer, but not as long as a 5400 speed drive will last.  And when RAID goes haywire, it's worse than a backlash on an an old bait casting reel, hi hi.........

I only ask that you read up on exactly WHAT RAID really is before sticking your neck in gillotine.

TTUL
Gary

---

### Post by nhasian on 2008-10-19
Sorry Kellemora, I have to disagree.

octotracy is on the right track.  he's got a single drive for his OS (dual booting) and wants to use a mirrored raid array for his data.  That redundancy will prevent him from losing his data if he has a hard disk failure which is not all that uncommon.  I had the hard disk in my laptop fail after only two months of use.

the only problem i see is that if you want to dual boot you cannot do a software raid array.  the raid must be idone in the hardware either in the motherboard bios or raid adaptor.

> **Kellemora said:**
> RAID 0 and RAID 1 are NOT what they are tauted to be!

Your data is no safer and could actually get mangled easier than using simple hard drives.

---

### Post by Kellemora on 2008-10-19
Hi Nh

OK, But I have a question to pose to you.
Why not stick with simple duplexing?

I think we will agree that RAID 0 is an accident looking for a place to happen.  RAID 1 is closer to what we are hoping for, and I know it can be configured different ways.  But no matter how you look at it, your still looking at s/2, and a .25% failure rate.  Albeit small, it's still present.

Duplexing (mirroring) allows one of the two drives to remain at rest most of the time, whereas RAID 1 is running both drives, in essence almost doubleing wear n tear on those drives.
There is no SPACE benefit of a RAID 1 system, it's still a mirror, same data on both drives, but both are running.

Whether you use duplexing or use Raid 1, you still have two equal sized hard drives both containing the same data.  Except in duplexing one of the drives is not working itself to death, which, if they are the same brand and age, both could fail at the same time too, rare, .09% but it happens.

Technically, it costs no more to move up to a RAID 5 system, if you compare the amount of SPACE you gain in the process.
Although mdadm will allow a 2 disk Raid 5 system, I wouldn't use less than 3 disks.

In Raid 1, s/2 you only have 1/2 of your total space, same as in duplexing.  But in Raid 5, it's n-1, so in essense you gain 1/3 more storage space than in a Raid 1 configuration.

Where my primary concern really is, is that new computers that come with twin drives and RAID on-board, those drives are OFTEN of the same brand, type and worse yet, the same LOT number.  

A properly designed RAID system 1 or 5 would NEVER use two drives in the array within the same range of Lot numbers.

My final point is, DON'T trust RAID 1 as your backup source!
I don't even trust RAID 5 as far as that goes.  Nor do many other folks either.

On my systems here, every computers drive is mirrored, and every mirror is backed up twice, redundant due to bad files overwriting the mirror before they are discovered to have gone bad.  So we also have archived sequential backups as well.  No file is replaced until AFTER the current file is determined to be correct.  A file must be changed to push the stack of sequential files off the backups, one at a time, depending upon how many slots are designated for each particular file.

Personally, I don't consider RAID 1 as a reliable backup system.  Especially if both of those drives came in that computer from the manufacturer.  They probably came from the same lot numbers, which I've already talked about.  I don't even backup to same brands just to be extra safe!

Just my 2 bits worth!

TTUL
Gary

---

### Post by sudo_chop on 2008-10-19
> **Kellemora said:**
> 
Duplexing (mirroring) allows one of the two drives to remain at rest most of the time, whereas RAID 1 is running both drives, in essence almost doubleing wear n tear on those drives.
 
I'm not sure where you are getting this stuff, but what makes you think duplexing shuts down a drive? If your drive is plugged in, it is spinning... full speed. If we are talking about the same duplexing we are talking about a more complicated RAID 1 that uses seperate controllers to protect against controller failure. I would really like to know just what you are talking about.
 
Simultaneous physical disk failure rate = astronomical

---

### Post by b0b138 on 2008-10-20
> **octotracy said:**
> My flatmate's managed to set up the mirror using mdadm.  But we can't get the array formatted and therefore can't mount it.  We've used gparted to try to format it and it just says

create new fat32 filesystem
>mkdosfs -F32-v /dev/mdop1
 >mkdosfs 2.11 (12 Mar 2005)
 >/dev/md0p1: No such file or directory

We're formatting it as Fat32 so that windows can hopefully see it. I can see the array in Computer but it isn't mounted.  Any ideas?

Regardless of what problems your having getting it formatted, windows will not be able to see it using mdadm for raid.  If your motherboard has raid built into it, you will have to use that for both ubuntu and windows to see it.  In windows, you'll install the driver and in ubuntu you'll install dmraid. If you do, set it up in windows first, and you can format as ntfs if you want

---

### Post by octotracy on 2008-10-20
I know that windows won't be able to see the raid1 - what I'm hoping for is that on the very rare occasions that I use windows I'd be able to read the data on the disks (which I know I'd see as separate drives)

My motherboard doesn't have raid built in.  I bought a sata raid card last year after my sole hard drive died last year and I almost lost everything (luckily I'd backed up because I'd been planning to do a reinstall of xp).  I've never been able to get the raid card to work - the array always fails after a few hours use.  We've looked into this and it seems to be a driver issue.  I'm not bothered about this.

I'd like to use raid for simplicity and I'm not so paranoid about losing data that I'm going to buy more drives and set up raid5.  I'd be quite happy with just the one back-up (eg two hard drives with the same data on them).  If there is a better way of doing this than raid, please tell me.  I'd thought about doing a back-u[ once a week, but don't know how to set it to just copy new data.

Overall, I seem pretty close with the raid, I just can't understand the formatting problem.  I think maybe windows is interfering with it - if in doubt, blame windows :)

---

### Post by handydan918 on 2008-10-20
> I'd thought about doing a back-u[ once a week, but don't know how to set it to just copy new data.


I think the tool you want is rsync. You can set it up to run as a cron job, and back up only changed data.

---

### Post by Kellemora on 2008-10-20
Well SC

I have 8 computers here, 7 of them contain dual drives (a small drive for the OS and the larger drive for data storage) and those drives are mirrored to a larger external drive for each computer and they ARE Syncronized as well.  2 of the main computers are INSTANT syncronization, now those external mirrored drives begin spinning the second you hit a key.  All the rest are time synchronized, so the external drives are asleep until they need to perform.

I don't see why you don't understand a simple technology that has been around for decades now?

I'm the only one in here right now (lunch time) and the other main computers external hard drive is flashing, which tells me it's taking a much needed nap.  All of the external hard drives on the other computers are sleeping as well.  Well I spoke to soon, it just hit 12:30 so they are starting up and checking to see if any data changed in order to synchronize if need be.

At 3AM, another program copies mirrors all the mirror drives to a single large drive in another room and to another off-site location.  You might even call that triple redundancy if you want to.

There are downsides to duplexing and mirroring, such as a changed file is changed on the mirrored drive as well.  If a file goes bad on it's own, it too will be copied to the mirror as a bad file.  So you just lost your backup copy.  Thus the reason for redundant backups, including incremental compounded backups that never delete the previous mirror until it scrolls off the space allocated for those files.

I don't remember off the top of my head, but I think rdiff allows this type of mirrored backup, maintaining todays file for a year or 30 days, and you can set year old files to drop, month old files to drop or even week old files to drop.  Mine will keep one mirror of certain files from each month or 12 copies.

But the thing is not how I have the extra computers around here set up, it's the main ones that duplex and synchronize darn near every keystroke.  In this case, if someone is working at the computer, the external drive is running.

I'm not a hard drive technician or designer, have no idea for sure what is going on inside that box.  But I do know it's not as hot when it's asleep, it don't have that vibration, and if it kicks in to sync and mirror and it takes a long time, they vibrate more and heat up.  

As far as having similar hard drives from the same lot number go out very near the same time, after I made my post I went and checked.  The odds of random hard drive failure, two drives at once is 0.09% as I posted for drives of the same lot number, which is an error.  The chances are exponentially greater.  Simultaneous don't mean diddly, its like comparing apples and oranges.  The question should be, what is the chance of both hard drives from the same lot number failing within the same 24 hour period, or during the same week, if it takes you that long to obtain, replace and restore your failed hard drive.
I think you will be surprised at how often this does occur naturally, not from external source problems!

We lost thousands of important images, non-replacable, due to a failed Raid 1 system, and the mirror drive for backup failed less than 6 hours later.  We discovered a glitch in the mirror to archive backup system that only saved links back to the failed mirror drive, not the actual files at it was supposed to do.  Another problem of using new software one is not yet familiar with and don't know the nasty bugs yet undiscovered in them.
There is no way a mirroring or backup system should backup only a link to the file it's supposed to be archiving.  There were no settings within the program to do this purposely.  Ergo a bug that cost us a lot of grief!

If Raid 1 uses 2 hard drives, so does duplexing and/or mirroring.  Uses up the same amount of space.  But you should also have another off-site backup of that data that does not get overwritten, just in case a file does become corrupt and the corrupt copy then appears on your mirror.

Western Digital, Maxtor, Seagate, etc. all provide free software with their external drives to do all kinds of things regarding backup, mirroring, duplexing, and software Raid which is almost the same thing as duplexing as the drives run anytime the computer is in use.
EMC Retrospect handles allmost all file types from the DOZE to Unix and all flavors in between. ext2/ext3 the SWAP file. and across LANs with no problems, so that's what we use here.

Hard drives last a whole lot longer if they are not spinning their guts out all day long.  The large Archive drives only run from around 3am until about 5am each day.  Unless we need to access them for something.

It's NOT new technology!  Virtually nothing I have here is new new, hi hi..........
Except for newer hard drives which are replaced faster than popcorn.  The decade old hard drives are still humming along just fine!

TTUL
Gary

---

### Post by octotracy on 2008-10-20
Aargh!

Thought I had it this time, but after setting up the raid again, when I tried to format the raid array, I got this..

Error informing the kernel about modifications to partition /dev/md0p1 -- Invalid argument.  This means Linux won't know about any changes you made to /dev/md0p1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/md0 (Invalid argument).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/md0.

Does this mean anything to anyone?  Rebooting doesn't help

---

