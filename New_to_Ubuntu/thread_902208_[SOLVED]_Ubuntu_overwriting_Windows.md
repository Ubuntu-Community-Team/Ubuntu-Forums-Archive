---
title: "[SOLVED] Ubuntu overwriting Windows"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by boltz101 on 2008-08-27
Hi guys,

I decided to start playing with Ubuntu after installing SuSe and not really getting on with it.

I was running Ubuntu from the CD and last night I decided to keep it and install it to the HD - when I installed it, I didnt get any messages about partitions etc, so I just assumed that it would create a partition and let me run 2 O/S (Ubuntu for me and Windows for my technophobe other half!).

Once everything was completed and I had messed with a few settings etc, I rebooted and I noticed that the Grub will only boot directly into Ubuntu, with no boot choice for Windows.

I did a bit of searching last night, ran a few commands (I'm quite a Linux n00b so the terminal is still quite foreign to me) and I couldnt find any way of changing the grub.

I also did the partition tool (g-part I think) and it showed up with 3 partitions, although I cannot figure out if any of these are Windows.

I couldnt care less about the Windows install to be honest, but I had ALOT of pictures and memories from over the years (baby being born, first steps etc) and I have never thought about backing up (yeah don't worry I wont make this mistake again!).  The problem is that my laptop is an Acer Aspire 3000 series, and I have a terrible feeling that the D (slave) drive that I had all of my pictures on was actually a partition.

I really do have a terrible feeling that I have lost everything, so please please help me to either find out where Windows is, where the files are stored, or how I can perform some kind of HD restore!

Thanks in advance.

---

### Post by AndyCee on 2008-08-27
Don't panic yet :)

You say there were 3 partitions in the partition editor? One would be where Ubuntu is installed (formatted ext3), one would be "swap", and the other could be windows or the OEM windows disk partition. Is "ntfs" on that line? How big is the partition?

In "Places" at the top of the screen, is there a disk? The windows partition may be available as a disk.

---

### Post by boltz101 on 2008-08-27
GParted shows 3 partitions:

/dev/sda1 - filesystem ext3 (size 35.69gb used 2.59gb, boot)
/dev/sda2 - filesystem extended (size 1.57gb)
/dev/sda5 - filesystem linux-swap

In Places I only have Computer (no mention of the documents in there), CD/DVD Creator and Disc (which is the Ubuntu installation CD).

---

### Post by mcduck on 2008-08-27
Actually Ubuntu by default likes to create the extended partition during the install, that would be the third partition (and it's now even mountable, justv a container for logical partitions).

I'm sorry to tell you, but that sounds a lot like you have actually erased your Windows install. The installer _does_ ask how do you want to partition the disk (use the whole disk, resize windows partition or manual partitioning). You must have missed that by accident and selected the option to use the whole disk.

There really isn't any easy way to restore, since the partiton is already overwritten by another file system. Somebody might be able to recommend you some rescue-CD that can recover files after re-partitioning, but personally I have no experience about those. Of course if your files are valuable enough to you then IBAS can most likely recover them, although with a high price..

---

### Post by boltz101 on 2008-08-27
Thanks for your reply - we have some Perl developers in our company so they know their way around Linux and Unix, they are going to look at it today at lunch time.

They say much the same as you, and think that I have screwed it up.

You mention IBAS - what is this?  To be honest I would explore any avenue to try and get the pictures back!

---

### Post by mcduck on 2008-08-27
> **boltz101 said:**
> 
You mention IBAS - what is this?  To be honest I would explore any avenue to try and get the pictures back!

Ibas is a company offering world-wide services for data recovery. If it can be satill recognized as disk, they can probably recover the files from it. (most liekly they can do it even if you can't recognize as disk any more, they were able to save data from hard disks from space shuttle Columbia which, as you probably know, exploded..)

But their services can be very expensive.. :/

[http://ibas.com/]("http://ibas.com/")

---

### Post by starcannon on 2008-08-27
This post lists free software for recovering photos, and worked for the guy that had a situation similar to yours.

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

Grab that, try not to use the affected hard drive for daily use until the files have been recovered, each time something is written to the drive a recoverable picture could vanish.

GL and let us know how it tuns out.

---

### Post by boltz101 on 2008-08-27
That is a fantastic thread and I will give it a try thanks very much!

---

### Post by ByteJuggler on 2008-08-27
> **boltz101 said:**
> That is a fantastic thread and I will give it a try thanks very much!

To add to what starcannon has said, I suggest you obtain/work with a liveCD to recover files to prevent all writing operations to the disk.  I also would suggest making an image of the disk onto another disk, if possible, to further protect the data on the disk from further accidental loss.  Personally I tend to use [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") for recovery situations, but the [Ubuntu rescue remix]("http://ubuntu-rescue-remix.org/") is also very good.  [This page here]("http://ubuntu-rescue-remix.org/node/54") is probably relevant to your predicament.

---

### Post by boltz101 on 2008-08-28
> **starcannon said:**
> This post lists free software for recovering photos, and worked for the guy that had a situation similar to yours.

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

Grab that, try not to use the affected hard drive for daily use until the files have been recovered, each time something is written to the drive a recoverable picture could vanish.

GL and let us know how it tuns out.

Just to give you an update on this - it worked!!  What an amazing tool, discovered partitions that I had deleted years ago.

I'd like to just say thanks and the person who developed that will be getting a little donation from me!

Thanks a million, now here's to reinstalling Windows (yuck!) for my other half, chucking Ubuntu on a partition this time, backing up data all of the time and also learning more about Ubuntu so that one day I might be able to give some advice out!

---

### Post by starcannon on 2008-08-30
Grats! and be sure to click on Thread Tools up to the right of this thread, and Mark as Solved.

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

