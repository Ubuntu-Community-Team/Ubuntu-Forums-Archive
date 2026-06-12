---
title: "Advice needed re repartitioning and moving home to /home (14.04)"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by xhepera on 2014-04-25
[COLOR=#333333][FONT=UbuntuRegular]I have installed 14.04 LTS on a laptop, in a dual boot configuration with Windows 7. HDD size is 500 GB. 
Before installing Ubuntu I used Gparted to get approximately a 250 GB partition for the Ubuntu installation.
What I would like to do now is give the root partition 30GB, increase the size of the swap partition, and create a separate partition for /home.
 I am used to using 10.04 (on an older laptop) but never did any repartitioning or moving on the Ubuntu partition, so I am an absolute beginner at doing this sort of thing. I've done a number of searches, which have served only to confuse me, or go way over my head, unfortunately. This is what I *think* I need answers to:

1. sda4 (Extended) is reported as not starting on a physical sector boundary. Should I "correct" this? If so, is it possible to do it without destroying the contents of my Ubuntu installation?
2. I found a guide to moving /home to its own /home partition here: [http://www.maketecheasier.com/move-home-folder-ubuntu/](http://www.maketecheasier.com/move-home-folder-ubuntu/). Will this work in 14.04? Is this method advisable?

This is what Gparted reports:

[IMG]http://i.imgur.com/00aC40c.png[/IMG][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]And this is how things are set up as viewed in the terminal:

[/FONT][/COLOR][IMG]http://i.imgur.com/p1imAac.jpg[/IMG]

---

### Post by Impavidus on 2014-04-25
1: I don't think that's much of a problem. Maybe somone knows an easy fix.
2: That guide looks OK. I always recommend [this one]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), but they are almost identical. You want to shrink sda5 to the left and create a new (logical) partition between sda5 and sda6.

---

### Post by oldfred on 2014-04-25
You do not write into the extended partition, so its location is not critical. It is all the logical partitions inside the extended that should be correct. But it only is a real requirement for new 4K drives and SSDs.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by xhepera on 2014-04-25
> **Impavidus said:**
> …
2: That guide looks OK. I always recommend [this one]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), but they are almost identical. You want to shrink sda5 to the left and create a new (logical) partition between sda5 and sda6.

Thank you. I've looked at the guide you suggested, and will likely use it.

---

### Post by xhepera on 2014-04-25
> **oldfred said:**
> You do not write into the extended partition, so its location is not critical. It is all the logical partitions inside the extended that should be correct. But it only is a real requirement for new 4K drives and SSDs.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). …

Ah, I see. Thanks for clearing that up about the extended partition. I checked the specs on the drive and it is a 512/4096. I've also looked over the links you provided. Thanks very much!

I'm going to leave this thread open for a bit until I get this done, in case I need to ask anything more, but I think I understand what needs to be done now. I'll mark it solved and close it after.

---

### Post by Impavidus on 2014-04-26
Note that shrinking a partition is slow and if anything goes wrong you could lose data. Make sure you have backups of your important files in your home directory. Don't bother about the system files. If anything goes wrong with them, reinstalling is the best option.

---

### Post by xhepera on 2014-04-28
Thanks again folks! Did it and I'm up and running with the config I want.

---

