---
title: "bad sector - can't resize ntfs partition"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by bjameswilliams on 2008-04-24
i want to resize this partition to free up space for ubuntu, which i am installing from the live disk, so that i can dual boot windows & ubuntu.

the installation from the live disk brings up a partition editor at one point but i'm not even given the option to resize & so i can't install ubuntu. i found that the reason for this is a bad sector on my hard drive.

it seems like there's got to be a way around this ... right?

---

### Post by Stefanie on 2008-04-24
you have to run chkdsk. in windows XP: start menu -> run -> type "cmd" without the quotes -> type "chkdsk -f" -> hit enter -> restart the computer 
I don't know about vista but there should be something similar to chkdsk i guess

i had exactly the same problem and i solved it this way.

---

### Post by swoll1980 on 2008-04-24
boot windows under my computer right click c:drive go to properties tools see if you can repair with disc scan

---

### Post by kansasnoob on 2008-04-24
I always run a "Scan Disk" utility first and then defrag.

GParted (the Ubuntu partitioner) is quite intuitive and will try to stop you from damaging the system you're repartitioning. If you've ever watched the defrag process in Windows you'll see those "unmovable" lumps of coal!

If windows says it can't be moved then GParted won't move it, they don't want to break it. I still use an old V-COM System Suite Utility to prep my Windows (up thru XP) for repartitioning.

---

### Post by twist2b on 2008-04-24
What you need to do sometimes is use a defrag. This moves ALL the information all to the front of the partition of Vista. (otherwise you have information all over the place).

OK, then you should try it again. You CAN create a partition by going into windows and right clicking my computer and select "manage" then select disk space or something (close to the bottom) then right click windows partition and select shrink.

---

### Post by bjameswilliams on 2008-04-24
none of this seems to be working! what am i missing here?

i ran chkdsk, restarted, let it do its thing, defraged (again), tried to resize the partition using the windows utility but couldn't find a 'shrink' option or anything like it, then restarted & booted ubuntu which still recognized the disk as having a bad sector.

what might i be doing wrong? any other suggestions? i appreciate everyone's help!

---

### Post by billgoldberg on 2008-04-24
> **bjameswilliams said:**
> i want to resize this partition to free up space for ubuntu, which i am installing from the live disk, so that i can dual boot windows & ubuntu.

the installation from the live disk brings up a partition editor at one point but i'm not even given the option to resize & so i can't install ubuntu. i found that the reason for this is a bad sector on my hard drive.

it seems like there's got to be a way around this ... right?

Use the gparted live cd to resize the partition.

Beware that this will take an very long time.

I'm resizing my external hdd from 450 to 150gb and gparted has been running non-stop for 3 days.

If you can't figure out how to do it, look through the gparted faq.

---

