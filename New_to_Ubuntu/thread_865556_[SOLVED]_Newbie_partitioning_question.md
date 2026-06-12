---
title: "[SOLVED] Newbie partitioning question"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by A2JC4life on 2008-07-20
I'm so glad to see this forum!  I've been trying off and on to get Linux working for me (various distros) for at least eight years, and I've never been able to find Linux users who can talk to me in plain English! lol  It all seems to be techie talk.  It looks like the folks around here can speak plain English. ;)

I have a partitioning question.  I will be setting up Ubuntu (or Kubuntu; I haven't fully decided which one yet) to dual-boot with Windows XP. The documentation says that the partitioning process will wipe out all data on the HDD, but the implication I get from the part about installing if you already have Windows installed is that manually adjusting the partition size will not necessarily do so.  So, here's my question: Although obviously I need to back up my data anyway, just in case, if I defrag and then manually adjust the size of my Windows partition, will it really wipe out all of my data, or will it leave the data at the front end of the partition alone?

I've had issues before with my backups not working properly (after they tested fine on multiple computers when first made), so I'm trying to judge just how much of a risk I'm taking with the data on my HDD - whether it *might* all be wiped out, or whether it will *definitely* all be wiped out.

---

### Post by tamoneya on 2008-07-20
if you follow the steps you laid out it will not touch the data at the beginning of the partition just like you said.  Then you can use the ubuntu or kubuntu liveCD to install.  During the installation tell the partitioner to install in the remaining free space on your harddrive.  Then it will configure the bootload and everything for you.

But as always you should backup when you are messing with partitions.

---

### Post by drs305 on 2008-07-20
> **A2JC4life said:**
> So, here's my question: Although obviously I need to back up my data anyway, just in case, if I defrag and then manually adjust the size of my Windows partition, will it really wipe out all of my data, or will it leave the data at the front end of the partition alone?

That is a sound plan and should work. I would go ahead and do the resizing outside of the ubuntu install and check the results before beginning to put a new system on the drive. Once you determine the action proceeded as you wished, install (k)ubuntu.

Welcome to ubuntu. We'll be here to answer your questions (in simple english most times). ;-)

Note: When your questions are answered you can mark the thread solved with the "Thread Tools" link at the top right of the original post.

---

### Post by Xerp on 2008-07-20
The Ubuntu installer can simply resize your existing Windows partition, if thats what you want :)

[https://help.ubuntu.com/community/GraphicalInstall#Select%20a%20Disk](https://help.ubuntu.com/community/GraphicalInstall#Select%20a%20Disk)

---

### Post by scragar on 2008-07-20
defrag once or twice, pop the live CD in, get past the first few options, and it'll start it's own little partitioning program, and let you choose from a few options, the most intresting will be: **Guided Resize** where you can adjust a sliding bar to decide disk space for windows and disk space left for windows, easy enough right?

---

### Post by A2JC4life on 2008-07-20
Thanks, all!  I feel a lot more confident knowing that my backup will actually be a BACKUP, and not the primary copy of my files!

---

### Post by Troll_the_Great on 2008-07-20
I would suggest to make a separate partition under windows (with Partition Magic for example) and install Ubuntu on that partition.About 15-20 GB should be enough.I did that and works like a charm.
Anyway, as usual, back up all your data before you proceed.
Cheers!

---

### Post by dhughes on 2008-07-20
The way I do it is:

 [LIST]
[*]Use Gparted or Partedmagic LiveCD to make two partitions (or three if /home is to have its own).

[*] Install Windows first, which I believe you *have* to do when dual booting Linux and Windows.

[*] Defrag Windows, just in case, although it is on a different partition.

[*] Install Linux to the other unused partition (or more if making a /home partition too).
[/LIST]

 If you are going to create or adjust partitions during the Linux install just use the free space or as mentioned adjust it to the size you want.

 Ubuntu won't lie, you can see it in its eyes.

---

