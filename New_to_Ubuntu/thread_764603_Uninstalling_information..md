---
title: "Uninstalling information."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by kdw008 on 2008-04-24
Hi, all--

I have not installed Ubuntu yet, but I definitely want to give it a try. I am certain I can install it and use a dual boot with Vista (apologies if my terminology is not correct!); my confusion comes in the possibility that I will want to uninstall it later, **without** having to delete all my files before using Vista again. I have been googling and searching around here but cannot seem to find a definitive answer, so sorry if this has been answered before.

I have a HP Pavilion laptop, which means that I do not have a Vista recovery disk. I understand I can buy one from HP for less than $20, but I also understand this disk gets rid of everything...? If I backup all my files and create recovery DVDs using the recovery disk creator on my machine **before** installing Ubuntu, will I be able to restore my laptop to how it is at this moment, should I decide Ubuntu is not for me? If not, is there any way I can make this happen?

Also, should I do a general cleanup of the laptop before beginning? Such as running CCleaner, defragmenting the disk, etc. etc.? If yes, what all is suggested?

I first used Linux on an ex's machine a few years ago, so I know I like it! I just want to be sure there is a way to undo things if I need!

Thanks everyone in advance!

---

### Post by kilroy423 on 2008-04-24
> my confusion comes in the possibility that I will want to uninstall it later

Chances are that if you are using Vista you will be uninstalling Vista after about 10 minutes on Ubuntu.

> If I backup all my files and create recovery DVDs using the recovery disk creator on my machine before installing Ubuntu, will I be able to restore my laptop to how it is at this moment, should I decide Ubuntu is not for me? If not, is there any way I can make this happen?

As for my experiences with Windows, all their backup features are garbage.  Your best bet is to just copy off what files you want and then just reinstall Vista if need be.  But, you can make a block copy of the disk in its present state and restore later(norton ghost is a decent Windows app)

I don't remember if HP ships with the Vista disk or not, if it does you can just reinstall from that, otherwise you will need to use ghost.

> Also, should I do a general cleanup of the laptop before beginning? Such as running CCleaner, defragmenting the disk, etc. etc.? If yes, what all is suggested?

Fragmentation is a Windows deal, you can run on Linux for years and only have about 2% fragmentation compared to months in Windows.  Although you will need to partition your disk to accommodate both Linux and Windows.  This can be done with the Windows cd or with the Ubuntu cd, I'm not too sure how NTFS is with resizing though.

> I first used Linux on an ex's machine a few years ago, so I know I like it! I just want to be sure there is a way to undo things if I need!

Just make sure and get any critical files off of your computer and you should be fine.

---

### Post by Tatty on 2008-04-24
Removing Ubuntu would comprise of three steps:

1. delete the ubuntu partitions
2. restore the windows mbr so you can boot into vista
3. expand your vista partition so it fills up the drive again


[slight detour]Its ridiculous that HP will not give you a CD to restore vista - even microsoft recommends that you re-install windows every 6 months.  grr, that kind of greedy money-grabbing control by corporations gets me mad *gets on my soapbox*.  Lol ok sorry for that detour.[/slight detour]

The thing you need to be prepared for is the possibility that something goes wrong with your install (or uninstall) as these are major changes you are committing to your hard drive.  Its not likely that something will go dreadfully wrong - but computers are computers.  If things get really bad then you might need to re-install vista anyway (although as i say, this is rather unlikely - just making you aware), so make sure you back up anything important.

Yes definately defrag before you install!  you should defrag at least 3 times before installing ubuntu.  A good chkdsk would be a good idea too.  This will all help to prevent corruption during partitioning.

---

### Post by Humph on 2008-04-24
I'd recommend taking a disk image (if you can, of course) using something like Acronis Disk Director Suite, or Norton Ghost prior to installing Ubuntu, just in case anything really bad happens. I'm a big fan of Disk Director and consider it probably the best $50 I've spent on a software product!

I don't know about Vista, but XP doesn't natively support (in Disk Management) resizing partitions. The Ubuntu LiveCD partition editor can help you with resizing your Windows partitions.

---

### Post by Tatty on 2008-04-24
> **Humph said:**
> I don't know about Vista, but XP doesn't natively support (in Disk Management) resizing partitions. The Ubuntu LiveCD partition editor can help you with resizing your Windows partitions.

The usual recommendation if you have Vista is to use the native Vista partition editor to edit the vista partition, because it can get upset if you use a different partition editor.


If you want to make a disk image before you do anything (seems like a good idea) then you can use partimage to do that - it is free and open source i believe.  I have never used it myself but it seems pretty straightforward to use.

---

### Post by Xiong Chiamiov on 2008-04-24
You may also want to check out the new [Wubi project]("http://wubi-installer.org/").  It allows you to remove Ubuntu in Windows just like any other program.

---

### Post by kdw008 on 2008-04-24
Yes, I am rather upset that computers do not come with a recovery disk. What is odd is that I ordered a laptop that had the option of coming with one, but it never shipped (no one believes my address is real :-|) but when I tried again, that option was gone. I missed it by a few days!

Anyway, thanks for the replies, everyone!

---

