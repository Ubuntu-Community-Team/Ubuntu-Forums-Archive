---
title: "partition question again"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by sheroxe on 2008-08-22
Ok so im installing ubuntu, i rebooted with the cd in, then selected install ubuntu answered some questions about time zone etc, and now i got to the partition part.

It gave me 2 options, one to delete windows and use all disk for ubuntu, and a manual option. I chose manual cause i want to keep windows too.

So a window appeared named "Prepared partitions"

Device...| Type | Mount Point | Format?..| Size.....| Used    |

/dev/sda
/dev/sda1  ntfs ....................(checkbox)  151460 mb  unknown
/dev/sda2  ntfs ....................(checkbox)  8578 mb    6400 mb

If i select sda1 or sda 2 i can either edit partition or delete.

If i select the first one (sda) i have the option "new partition table"

What am i supposed to do here? help please :confused:

---

### Post by snowpine on 2008-08-22
> **sheroxe said:**
> Ok so im installing ubuntu, i rebooted with the cd in, then selected install ubuntu answered some questions about time zone etc, and now i got to the partition part.

It gave me 2 options, one to delete windows and use all disk for ubuntu, and a manual option. I chose manual cause i want to keep windows too.

So a window appeared named "Prepared partitions"

Device...| Type | Mount Point | Format?..| Size.....| Used    |

/dev/sda
/dev/sda1  ntfs ....................(checkbox)  151460 mb  unknown
/dev/sda2  ntfs ....................(checkbox)  8578 mb    6400 mb

If i select sda1 or sda 2 i can either edit partition or delete.

If i select the first one (sda) i have the option "new partition table"

What am i supposed to do here? help please :confused:

DON'T REFORMAT sda1 OR sda2! You will lose your Windows installation! Before you proceed, please take the following steps:

1) BACK UP everything on your Windows partitions.
2) EDUCATE YOURSELF on how partitions work. Here is a good page that discusses the different options: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) Ask questions; we are here to help!

---

### Post by aloshbennett on 2008-08-22
/dev/sda is your hard disk. You have two partitions in it - sda1 (150 GB) and sda2 (8GB).

Where do you have your windows installed?

---

### Post by Gone fishing on 2008-08-22
It seems that you have 2 Windows partitions a large one and a small one do you have a C: and a D: drive in Windows?

I would suggest that you download gparted and burn to a CD or use gparted from the install CD and resisize the large ntfs partition then reboot the ubuntu install CD and let it install into the free space

---

### Post by sheroxe on 2008-08-22
i guess it's installed in the 150gb one, when i log in at windows and open my pc the small partition is called HP_RECOVERY

---

### Post by sheroxe on 2008-08-22
yes ai hace a C: drive and a D: drive (this one is called hp recovery)

---

### Post by snowpine on 2008-08-22
The most foolproof thing you can do is let the Ubuntu installer resize your windows partition and create the needed partitions. When you get to the partitioner screen, you should see options like "guided install--entire disk," "resize ___ and use recovered space," and "manual". If you don't see the "resize" option, you may need to defragment your windows partition (and/or free up some space if it is getting full). 

You should still back up your Windows data and check out the tutorial I linked to, but this option is safer than trying to set up the partitions yourself.

---

### Post by bobnutfield on 2008-08-22
DON'T REFORMAT sda1 OR sda2! You will lose your Windows installation! Before you proceed, please take the following steps:

BE WISE!  TAKE SNOWPINE'S ADICE.  Do not do anything more until you have prepared your hard drive for your Ubuntu installation.  It appears as though you have not created a partition for Ubuntu yet.  While you can do that from the install cd, I personally find it easier and safer to prepare my disk with gparted prior to attempting an install.  As snowpine has advised, back-up your windows data, defragment it and then prepare a partition for Ubuntu.

---

### Post by sandysandy on 2008-08-22
Defragement windows partitions.

Backup data.

for creating new partitions u can also use gparted (burn as iso image on CD)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

u will basically need one  [COLOR="Red"]/ [/COLOR]root partition (ext3) and one [COLOR="red"]SWAP[/COLOR] partition.

regards

---

### Post by sheroxe on 2008-08-22
Ok i quitted installation already.

About defragment...i did that yesterday and it took like 6 hours and never finished so i cancelled it. Any idea why it takes that long?

---

### Post by bobnutfield on 2008-08-22
> **sheroxe said:**
> Ok i quitted installation already.

About defragment...i did that yesterday and it took like 6 hours and never finished so i cancelled it. Any idea why it takes that long?

A large highly fragmented drive can easily take 6 to 8 hours to dfrag.

---

### Post by ajgreeny on 2008-08-22
1  Defrag windows 2 or 3 times to be sure, and **BACKUP**.
2  Boot Ubuntu liveCD.
3  Go to System >> Administration >> Partition Editor.
4  Click on the large windows partition (150GB) and shrink it to leave room for Ubuntu install, perhaps 100GB for windows and 50GB for Ubuntu, but it's up to you.
5  Format the empty space into two ext3 partitions, 49GB for / (root) and 1GB for swap.  These are example sizes.
6  Run installation of Ubuntu from liveCD, and when you get to partitioning choose Manual, where you will see the new partitions you made, and will be able to choose the mount point of / for the 49GB and swap for the 1GB.
7  Let the system install itself, and welcome to Ubuntu!

You can of course vary the partition sizes if you wish, but I have given these as examples of what would work on the size of disk you have.  You could also add other partitions such as /home, but for the moment I suggest you leave it as simple as possible, with just the two.

Good Luck!!  It's not really as scary as it may seem.

---

