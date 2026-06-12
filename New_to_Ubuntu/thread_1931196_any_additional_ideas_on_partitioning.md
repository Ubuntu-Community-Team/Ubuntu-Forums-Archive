---
title: "any additional ideas on partitioning?"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by anewguy on 2012-02-25
I kinda had a boo-boo with my computer - I think I blew part of it on a power spike from, of all things, a old large vacuum cleaner plugged into the same strip.  At any rate, I couldn't find what was wrong real quick, so I just said to heck with it for now and went to MicroCenter to get the parts for a better one anyway.  That being said, I now have a single 1.5TB drive, instead of a 250gb drive.

I've always tried for the last several installs to put a partition for swap, a partition for root and a partition for /home, since it's my understanding I can install (instead of update) with each new release as I have been and it wouldn't affect my home folder.

But now I have this big drive.  Obviously I still want swap and / in their own partitions, but I wonder if I need to do more than just /home.  One thing I want to do is get my vhs tapes and my existing dvd collection to disk so I can use this as a media server as well.  With that in mind, am I better off with also adding something like /data (if that's possible) so I can store my movies, etc., in that partition and not lose it as well?

Thanks in advance!

Dave ;)

---

### Post by Jake5 on 2012-02-25
I don't think that your question should have been asked in the Beginner talk forum, but I am glad It was. What an excellent idea! I have had trouble in the past adding more than three partitions, but thats probably due to lack of experience. I have a 2Tb external that i use as a media server. I think its just simpler to backup everything to when I have to reinstall, just click and drag. But it would be nice to not have to...I'll give it a try and see what I can come up with, may take a couple of days to get back to you...busy weekend...If you get it figured out beforehand...send me a pm with the deet's.

---

### Post by SuaSwe on 2012-02-25
I've wondered about this too - how would such a partition be set up? Awaiting a response on tenterhooks! :D

---

### Post by Paqman on 2012-02-25
You can add as many partitions as you like, and call them anything you like. You could create /data, /lolcats and /1337haXX0r if you wanted.

There is a limit on most machines of four partitions per drive, but you can get around that by creating one partition as an "extended" partition. Inside that you can stuff as many other partitions as you like.

To set up custom partitioning schemes use the "manual partitioning" option during setup. It's pretty straightforward.

Alternatively if you've already got your OS installed you can boot up into a LiveCD or USB, open up the Partition Editor, right click on any swap partitions and "swapoff", then make any changes you want. You'll then need to boot into your actual system and add an entry to /etc/fstab if you want to mount these new partitions automatically at boot time.

---

### Post by Elfy on 2012-02-25
I've not bothered with seperate home for a long time.

Shouldn't be needed anymore - the installer will recognise and keep the /home within / as long as you don't tell it to format.

I have a couple of partitions/drives mounted at boot.

As PAqman says - fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You might need [chmod]("http://ss64.com/bash/chmod.html") or a root nautilus to deal with permissions of the folders - but it's all fairly simple.

---

### Post by anewguy on 2012-02-25
I know it's probably lazy, but as long as an install doesn't blow away my /home I might as well go with 1 partition.  It's the only reason I ever went with more than 1 (besides swap of course, and with 16GB I would assume it could almost be non-existent as well).

Thanks for the input!  Will make setting up the new machine even easier!  It probably makes no difference to anyone but me, but this 1 is going to be all Ubuntu - no dual boot, etc..  If I get the old machine running again sometime it would still be dual-boot with Windows 7.  Truth of the matter is that if I could get my Family Tree Maker running respectfully again in Wine or 1 of the other tools.

At any rate, thanks for the input everyone!

Dave ;)

---

### Post by Paqman on 2012-02-25
> **anewguy said:**
> Truth of the matter is that if I could get my Family Tree Maker running respectfully again in Wine or 1 of the other tools.


Try GRAMPS, it's in the repos and will read and output to Family Tree Maker format.

---

