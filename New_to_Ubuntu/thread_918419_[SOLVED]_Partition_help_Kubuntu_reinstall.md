---
title: "[SOLVED] Partition help Kubuntu reinstall"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by AirWreck on 2008-09-12
I'm a week into Kubuntu and trying to reinstall it after a little "mishap" this morning.  I'd like to try to reinstall it with a separate home partition this time.  I've checked all the threads and tutorials but they all gloss over extra partitions as "advanced" and then move on to the basic install.

XP partitioned is installed in a 24gb part.  With the remaining 13gb of space, I want to create three parts, root, home and swap.

The "guided install using free space" seems to only create a basic root and swap config.  I think I've got the Manual option figured out but could someone confirm my thinking?

I'm having to type this from my notes of the screens so my questions won't be word for word....

1)  create a /root, ext3 file with mount point as / and it would be logical vice primary because the XP is primary in a dual boot scenario?  Say 10gb for now.

2)  create an ext3 file with mount point as /home and its logical?  2gb as a test.

3)  create a swap file, mount point swap, logical?  1gb (only 512mb RAM on this old machine).

Many thanks!

---

### Post by Locutus_of_Borg on 2008-09-12
delete all partitions when you get into the menu for partitioning

click on the free space and choose create

make it of type ext3 and mount it at /
make it about 20-30 GB

click on free space that is to the right of the partition you just created
make it ext3 and mount it at /home
make it the rest of your disk less 1-2GB

click on the final bit of free space and make it your swap

make them all primary

you only need a logical partition if you plan on having more than 4 partitions in total

---

### Post by AirWreck on 2008-09-13
Thanks, that worked great!  I'm replying from back over on the Kubuntu side of the fence so life is good;)

Another question related to the separate home partition:

I'm just playing for a few days on this old laptop, trying to learn as much as possible before my new one shows up and I do a clean install.  I know there are reasons for and against this if it is indeed possible, but can I just replace these folders in this new home directory with those from my original Kubuntu install that I've been working on this week? 

Thanks!

---

### Post by AirWreck on 2008-09-16
Found another thread that solved this for me.  /Home only has user settings.

---

