---
title: "More space to /home"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Sarys on 2012-12-12
Hey I was just wondering is it possible to take some space from / (root) to home?
My root partition is 22,9 Gb and my home is 29,2 Gb but it's running out of memory. My root on the other hand has 15 Gb free space. My linux in installed inside extended partition.

---

### Post by drmrgd on 2012-12-12
You can do it.  First (and very importantly!!!) back up your important data.  When playing around with the partition tables, it's always a possibility that something goes awry and you'll lose your data.

The other thing is that it's much more difficult if the two partitions are not near each other.  You can't take space from the start of the disk and just move it to the end of the disk for example  

To do it, just boot to a live CD (you can't change partitions on a mounted device).  Launch Gparted, and shrink the root partition.  This will leave unallocated space that you can then add to the /home partition by just increasing its size to take up that extra space.  

The procedure could take a little while as the system possibly needs to re-write and move data around to accommodate the partition shrinking.  Don't iterrupt this or else you'll lose your data and have to reinstall.  With the small sizes you mention, though, shouldn't take too long.

---

### Post by audiomick on 2012-12-12
Just to be clear: you have separate partitions for / and /home?

It is no big drama to shrink the / home partition and increase the /home.

You will need to boot from a live CD or USB stick (USB if you can; it runs much faster...). You cannot do partitioning operations on a mounted partition. Since one of the partitions you want to change is the system partition, you will need to boot from somewhere else to work on it. If it were, for instance, your /home partition and a data partition or something, you could work from the system itself and unmount the partitions whilst working on them.


The tool you need is Gparted. This is installed by default on the Ubuntu CD/DVD/USB although it is no longer in the install itself by default. You can also make a dedicated gparted CD/USB, boot to that and work from there.
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

You should backup anything critical before you start. Partitioning always carries a certain risk, so one should take precations. Having given the mandatory warning, I must say that I have never had problems. I have, however, seen posts here with things like "during the process, my little sister turned off the computer", or "during the process, the power went off"...

Don't make your / too small. Leave it with 15GB if you can, or at least 10. This install has only used about 4GB in /, but I recently had to expand the / for a friend of mine because her 9GB or so hat gotten full. If you make your / small, then keep an eye on it. The system does grow with time, and you can bet that you will run out of space at the most inconvenient moment possible. On my friend's computer, it was when she told it to do a version upgrade and it run out of space in the middle of that. I had to re-install...

---

### Post by Sarys on 2012-12-12
> **drmrgd said:**
> You can do it.  First (and very importantly!!!) back up your important data.  When playing around with the partition tables, it's always a possibility that something goes awry and you'll lose your data.

The other thing is that it's much more difficult if the two partitions are not near each other.  You can't take space from the start of the disk and just move it to the end of the disk for example  

To do it, just boot to a live CD (you can't change partitions on a mounted device).  Launch Gparted, and shrink the root partition.  This will leave unallocated space that you can then add to the /home partition by just increasing its size to take up that extra space.  

The procedure could take a little while as the system possibly needs to re-write and move data around to accommodate the partition shrinking.  Don't iterrupt this or else you'll lose your data and have to reinstall.  With the small sizes you mention, though, shouldn't take too long.

Unfortunatelly I can't backup my data

---

### Post by audiomick on 2012-12-12
> **Sarys said:**
> Unfortunatelly I can't backup my data

Absolutely no possibilites? Log on to Ubuntu One, for instance? Or drop box?

Borrow an external drive from someone?
Buy a couple of USB sticks?
Even a couple of CD's or DVD's and burn a backup to them?

It's up to you. If there is nothing on the computer that will really hurt if you lose it, just go ahead.

If there is anything really critical on there, you should have a backup of it anyway (says he with the worst backup practice in the world...).
Hard drive failures happen, even when you don't do any partitioning work on them. Or, to put it another way, every hard drive will fail in the end.

If the computer has internet access, maybe Ubuntu one, dropbox or one of those might be good for you. With the free space they offer, you wont be able to back up everything, but it might be enough for the really important things. Failing that, think about buying a large USB stick or an external drive.

---

### Post by vanadium on 2012-12-12
If you can't backup your data, then your data have no value to you. Your disk could fail any moment, and then your data will be gone. If you value your data, find a backup solution at once.

For such relatively small volumes, I would not maintain a separate hope partition anyway. I would have one single partition, so both the system and /home can use the space they need.

---

### Post by Sarys on 2012-12-12
> **audiomick said:**
> Absolutely no possibilites? Log on to Ubuntu One, for instance? Or drop box?

Borrow an external drive from someone?
Buy a couple of USB sticks?
Even a couple of CD's or DVD's and burn a backup to them?

It's up to you. If there is nothing on the computer that will really hurt if you lose it, just go ahead.

If there is anything really critical on there, you should have a backup of it anyway (says he with the worst backup practice in the world...).
Hard drive failures happen, even when you don't do any partitioning work on them. Or, to put it another way, every hard drive will fail in the end.

If the computer has internet access, maybe Ubuntu one, dropbox or one of those might be good for you. With the free space they offer, you wont be able to back up everything, but it might be enough for the really important things. Failing that, think about buying a large USB stick or an external drive.

All I can lose (from linux side) is games (on windows side I have my travel pics)

---

### Post by audiomick on 2012-12-12
> **vanadium said:**
> For such relatively small volumes, I would not maintain a separate hope partition anyway. I would have one single partition, so both the system and /home can use the space they need.

Yes, opinions are divided on that. I always install with a separate /home. Has saved me some messing around a number of times. But I wont launch into a discussion about that here.

> **Sarys said:**
> All I can lose (from linux side) is games (on windows side I have my travel pics)

That's the thing: if you are doing partitioning, you should back up the important stuff ***_from the whole drive_***. If your partition table gets corrupted, it could also give you trouble with your windows install. As I have already indicated, though, this is a precaution. You can assume that your partitioning will work without a problem, but you should take the precaution anyway. Like wearing a seatbelt when you drive in a car.

As far as backups goes generally, if your pictures are all on the windows partition, that is even more reason to get them backed up. On the linux side of your install, if your system dies, you still have the stuff in the /home partition. On the windows side, unless you are using a separate data partition there, if the Windows dies, you will lose the files when you re-install it. There is still, regardless of which side of things the files are on, the thing that every drive dies in the end. Is it a laptop? What if you drop it?

---

### Post by Sarys on 2012-12-12
> **audiomick said:**
> Yes, opinions are divided on that. I always install with a separate /home. Has saved me some messing around a number of times. But I wont launch into a discussion about that here.



That's the thing: if you are doing partitioning, you should back up the important stuff ***_from the whole drive_***. If your partition table gets corrupted, it could also give you trouble with your windows install. As I have already indicated, though, this is a precaution. You can assume that your partitioning will work without a problem, but you should take the precaution anyway. Like wearing a seatbelt when you drive in a car.

As far as backups goes generally, if your pictures are all on the windows partition, that is even more reason to get them backed up. On the linux side of your install, if your system dies, you still have the stuff in the /home partition. On the windows side, unless you are using a separate data partition there, if the Windows dies, you will lose the files when you re-install it. There is still, regardless of which side of things the files are on, the thing that every drive dies in the end. Is it a laptop? What if you drop it?

I can back up my drive when I get back home 20th dec. But now that I think about it how to h**l I'm supposed to back up my desktop back home since it hace 500 Gb drive and I'm gonna buy 1 or 2 Tera byte disk to replace it (or just use the 500 Gb as boot disk for xp, 7 and ubuntu)

---

### Post by audiomick on 2012-12-12
> **Sarys said:**
> I can back up my drive when I get back home 20th dec.

Are you travelling? Can you get a hold of a USB stick? Perhaps you can get one of them, and just shovel a bit of data off onto there to ease the space problem until you get home.

>  ...to back up my desktop back home since it has a 500 Gb drive and I'm gonna buy 1 or 2 Tera byte disk to replace it (or just use the 500 Gb as boot disk for xp, 7 and ubuntu)

I would use the new drive as the main one. Install everything on it, get it all set up, and then transfer the files from the old drive to the appropriate place on the new. I would then use the 500GB drive to backup to. If you do your backups as compressed files (.tar), then that should be enough room. 

The main thing is to not have really important stuff on only one drive. Having it on two different drives in one machine is already good enough. Having your stuff on two drives in two different locations is, of course, better. There might be a fire, or a burglary, or something. But the main thing is to have a second copy should the drive fail.


If the desktop can't take both drives, think about getting an external enclosure for the second drive.

With both of those drives in the desktop, you should also have room to back up the laptop to the desktop.

---

### Post by vanadium on 2012-12-12
As a temporary lapstop, you could use some free space in the root partition to store data (create a directory there, change the owner to your user account and create a symbolic link to it in your home directory). Once home, you can make a decent backup and repartition without risking your personal data.

---

### Post by Sarys on 2012-12-13
> **audiomick said:**
> Are you travelling? Can you get a hold of a USB stick? Perhaps you can get one of them, and just shovel a bit of data off onto there to ease the space problem until you get home.



I would use the new drive as the main one. Install everything on it, get it all set up, and then transfer the files from the old drive to the appropriate place on the new. I would then use the 500GB drive to backup to. If you do your backups as compressed files (.tar), then that should be enough room. 

The main thing is to not have really important stuff on only one drive. Having it on two different drives in one machine is already good enough. Having your stuff on two drives in two different locations is, of course, better. There might be a fire, or a burglary, or something. But the main thing is to have a second copy should the drive fail.


If the desktop can't take both drives, think about getting an external enclosure for the second drive.

With both of those drives in the desktop, you should also have room to back up the laptop to the desktop.


My desktop has space for 3 hard drives. But yeah I was told that you should have back up in at least 3 places if you care about your data. For example in my school our teachers lost all of their email because the mail servers hard disk failed. They did have backup disk but it failed at the same time.

---

### Post by audiomick on 2012-12-13
> **Sarys said:**
>  back up in at least 3 places if you care about your data. For example in my school our teachers lost all of their email because the mail servers hard disk failed. They did have backup disk but it failed at the same time.

Bad luck to have two disks fail at once. I suppose if the power supply goes feral, it might take them all out...

Yes, separate locations is of course better, but two drives in one machine is still better than only one.

---

### Post by Sarys on 2012-12-13
> **audiomick said:**
> Bad luck to have two disks fail at once. I suppose if the power supply goes feral, it might take them all out...

Yes, separate locations is of course better, but two drives in one machine is still better than only one.

Agreed

---

### Post by Sarys on 2012-12-17
But how to back up ubuntu and win 7 so that they don't take too much space?

---

### Post by 3rdalbum on 2012-12-17
> **Sarys said:**
> But how to back up ubuntu and win 7 so that they don't take too much space?

Don't back up your whole operating system; just back up the files in your /home and My Documents, My Music, My Photos etc.

An external hard drive is a good bet. I actually have an internal hard disk and a hard disk dock; the hard disk sits on the dock, and the dock plugs into the computer's USB port. The dock accepts any SATA hard disk and it's trivial to pull the disk out and put a different one in.

If you're getting a new hard disk, why not consider putting your operating systems on the 500 gig, and your /home on the 1 TB? That's similar to what I do. Or if you can really only spare 40 gigs for Ubuntu, use only one partition for Ubuntu. You can still do a clean install without losing your files.

---

### Post by fdrake on 2012-12-17
just a question: wouldn't be easier and faster to take some spage from your root-partition, creat a new partition ext3 or fat and then mount the partition automatically with fstab. In the end the results it's the same more space for your data....

---

