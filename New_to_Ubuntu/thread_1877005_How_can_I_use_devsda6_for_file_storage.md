---
title: "How can I use /dev/sda6 for file storage?"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by Kellemora on 2011-11-07
Hi Gang

I have 6 partitions, wanted to use partition /dev/sda6 ext3 for file storage and am hitting a brick wall.

sda1 ntfs /media/XP-Pro-MCE
sda2 ext3 /media/Ubuntu-8.04
sda3 ext3 /     /Ubuntu-10.04
sda4 extended
sda5 linux-swap
sda6 ext3 /media/Debian-Misc

I cannot create a folder on sda6, that option is grayed out.
Is it because it has /media/ associated with it?

I wanted to Copy a rather large 125 gig file folder onto this unused 185 gig partition.

I know I could do this on 8.04 just by creating a folder and copying to it.  But it was an empty formatted partition named /Misc/.

Thanks
TTUL
Gary

---

### Post by TeoBigusGeekus on 2011-11-07
Gain ownership of the partition's mount point:
```
sudo chown -R yourusername: /media/Debian-Misc
```

---

### Post by Kellemora on 2011-11-07
Thanks TBG

Tried that, didn't get any error messages, but I can't see that it made any difference coming in from My Computer.

But Wait, now I see TWO folders in PLACES both with the same name, except OK, one is now open-able and I can create a folder in it.

Thanks!

I just hope things don't run in THREES today, we lost our file servers main drive last night and the backup failed so the backup drive is blank.
I want to download the offsite files from last Thursdays backup so I have an on-site copy.
RSync is always dealing me fits, I can fetch and save with no problems, but I've never been able to PUT a file anywhere and have it retain vital information needed to make the files work.

Again, Many Thanks, and for the quick response also!

TTUL
Gary

---

### Post by Paqman on 2011-11-07
> **Kellemora said:**
> wanted to use partition /dev/sda6 ext3 for file storage and am hitting a brick wall.


In Linux, everything is represented as a file. So /dev/sda6 is the actual device, but represented as a file. But you can't put your files there, you have to put them into the filesystem that's on /dev/sda6, which is mounted at /media/Debian-Misc.

It's a bit of a subtle difference, but just remember that anything in /dev is not actual stuff you can interact with, it's just Linux's way of handling devices. The reason it does it that way is that the actual device will always be in /dev, but you can mount the filesystem (or even just parts of it) to any location you want. The default location if you don't specify one is /media for removable devices.

---

### Post by Kellemora on 2011-11-11
Thanks Paqman

You know, I've read that a thousand times if not more and cannot seem to get it to work for me in that light.

If I do understand it correctly, it does not matter Where a Device (EG: hard drive) is located, provided you have the access to it so that it can be Mounted on the computer you are using.

Consider this scenario for a brief moment and see if you can figure out where I'm going wrong.
I will also give the solution I've been using, since the proper method does not seem to work for me.

First, we have the computer I am at doing my work, e-mail, writing, editing, etc.
Next, I have a second computer where I store all of my files on an external hard drive connected to that computer.  I call this my File Server even though technically it really isn't.  More on this later.
Third I have a third computer with an external hard drive off-site to mirror my data for safe keeping.  It gets more involved than this, but this is enough to suffice for my problem.

I do a lot of things, writing, editing, e-mails etc. on my main computer here that when finished I want to Save to the external drive on the second computer, exact copy of same, not a backup to avoid confusion.
I also work on files that are stored on the second computer by accessing them directly.  Some work this way, some don't.
For example, I can open an existing text file, edit and save it back, no problem.  I cannot edit and save a CAD/CAM file directly.  I have to first copy the file to my computer, work on it, save it on my computer, then copy the file back to the other computer.

Now here is where things get really crazy!
I want to use RSync to copy my folders from my computer to the file storage computer, then from the file storage computer to the off-site computers external hard drive.

What I've learned about RSync is that you cannot PUT a file anywhere.
But you CAN Fetch files with ease and maintain ALL of the permissions.

In other words, I cannot sit at my desk, mount the file servers external drive and/or the off-site computers external drive and have RSync write to them, PUT my files from this computer ONTO those computers HD's.

My solution for this problem that works takes quite a bit of extra work to accomplish.
I go TO the computer, in this case computer #2 and run RSync from that computer to FETCH the files from my main computer #1 and store those files on it's own external hard drive.
THEN I go TO the off-site computer #3 and FETCH the files from the external hard drive on computer #2.
When I do it this way, all permissions, dates, etc. stay intact and the files are accessible by all computers I use.

Now, if your (and everyone's statements) that it doesn't matter WHERE a hard drive (or actually the file on it) is Located, as long as I MOUNT that File System on my computer, Linux is supposed to see it the same as if the hard drive was on my own computer.

If that statement were True as Claimed, then I should be able to Save a File to that File System just as easily as I do to the Hard Drive physically connected to this computer.

RSync will save a file on this computer to an external hard drive connected to THIS computer without a single problem.
But it will NOT save a file to the external hard drive on any other computer without changing or deleting all the file type information and permissions necessary to use it.

I know it's probably something I don't know or understand that is causing me all these problems.  But the way I look at it, IF I can save to the Hard Drives connected to this computer, and if Mounting a Hard Drive is supposed to be the same as if it were connected to this computer, then using RSync to simply COPY those Files from Computer A to Computer B should not cause any problems.  The exact same settings in RSync should apply to the mounted drive as it does to the attached drive.

Hope you can make some sense of what I'm saying here!

By the way TBG's instructions worked perfectly for me to do what I needed to do.  Copy a failing HD to this computer for safe keeping.

Maybe that is where I'm going wrong?  Maybe I have to have permissions set differently on a drive on another computer for RSync to work properly.

I LOVE Linux, using almost nothing but now.  Have XP in Virtual Box for my accounting and that's about the only thing still handled in the Doze.
Well, that and changing toner cartridges when needed in the printers.  Even the on-board printer controls on the printers themselves don't bring the right toner cartridge to the front to change them.  So we use their Doze program to cycle the spent cartridge to the front.

Thanks for any insight you can give me!

TTUL
Gary

---

