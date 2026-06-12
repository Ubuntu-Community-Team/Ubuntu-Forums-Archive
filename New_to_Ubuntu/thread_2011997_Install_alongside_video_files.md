---
title: "Install alongside video files?"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by FuneralQueen on 2012-06-28
Hey guys :)

Hopefully an easy to answer question!

I'm setting up a media-center type PC with Ubuntu. I have 1 HDD ready, with a whole bunch of videos.

How exactly do I go installing Ubuntu alongside these videos without deleting everything?

I've been trying to figure out the partitioning option in the install menu but I keep getting the "No root file system defined".

Do I need to remove the HDD from the case and manually partition it in Windows first??

Thanks to anyone who can help :)

---

### Post by MG&amp;TL on 2012-06-28
My personal suggesstion is to backup the videos to somewhere else, just install ubuntu on the drive, then copy the videos back to your home folder once installed. Don't take risks with your data.

---

### Post by vidtek on 2012-06-28
> **FuneralQueen said:**
> Hey guys :)

Hopefully an easy to answer question!

I'm setting up a media-center type PC with Ubuntu. I have 1 HDD ready, with a whole bunch of videos.

How exactly do I go installing Ubuntu alongside these videos without deleting everything?

I've been trying to figure out the partitioning option in the install menu but I keep getting the "No root file system defined".

Do I need to remove the HDD from the case and manually partition it in Windows first??

Thanks to anyone who can help :)

FuneralQueen (nice)

Use gparted from a live cd to resize and move the present partitions.

Be aware any partitioning tool carries the risk of total data loss.

Create some free space - I usually have a root of 20gb and a separate home partition of 40gb. use the ext2/3/4 or journalised format for them.  Your home partition is where all your desktop settings, documents pictures etc are stored, and is reusable should your o/s give problems and you need to reinstall the o/s.


After you've done this do a normal install.

Best of luck, Tony

---

