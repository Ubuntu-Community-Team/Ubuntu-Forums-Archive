---
title: "Alternatives to gparted and dban"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Merps on 2008-11-15
Hey

I tried Gparted and it doesn't seem to format the hdd properly.  Dban does but it takes 2 hours +.

Is there another ISO to download that can format a hdd in less than 2 hours?

Regards

---

### Post by handydan918 on 2008-11-16
> I tried Gparted and it doesn't seem to format the hdd properly.
Huh? 
How was the format "improper"?

What are you trying to do? gparted is a fairly mature piece of code...it hasn't been beta for years...

---

### Post by Keen101 on 2008-11-16
If you are formatting a windows vista drive, then a lot of people are recommending vista's partitioner to shrink the partition...

beside that i would still recommend gparted over any other partitioning software I've tried. I do prefer the live-cd version though. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Merps on 2008-11-16
> **handydan918 said:**
> Huh? 
How was the format "improper"?

What are you trying to do? gparted is a fairly mature piece of code...it hasn't been beta for years...

with Gparted there is no 'format entire disc option', it seems to be designed for partitions not disc management utils.

---

### Post by handydan918 on 2008-11-16
> **Merps said:**
> with Gparted there is no 'format entire disc option', it seems to be designed for partitions not disc management utils.

Well. 
Did you try deleting all the partitions and then formatting?


Bet it works...

---

### Post by Merps on 2008-11-16
> **handydan918 said:**
> Well. 
Did you try deleting all the partitions and then formatting?


Bet it works...

hey handydan, deleting all the partitions doesn't destroy the data on the disc, and I didn't see the 'format entire disc' option.

---

### Post by Merps on 2008-11-16
> **Keen101 said:**
> If you are formatting a windows vista drive, then a lot of people are recommending vista's partitioner to shrink the partition...

beside that i would still recommend gparted over any other partitioning software I've tried. I do prefer the live-cd version though. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

hey thanks keen i don't have a Vista disc, but the problem with Gparted is that it is a Disc Partioning tool, not a Disc Formatting utility, I need to wipe the whole Disc, not just rearrage partitions.  Dban works but it takes a minimum of 2 hours +, way too long for me.

---

### Post by rzrgenesys187 on 2008-11-16
> **Merps said:**
> hey thanks keen i don't have a Vista disc, but the problem with Gparted is that it is a Disc Partioning tool, not a Disc Formatting utility, I need to wipe the whole Disc, not just rearrage partitions.  Dban works but it takes a minimum of 2 hours +, way too long for me.

You can wipe the disk and reformat it with gparted.  Run the ubuntu live cd and then open up partition editor (It's under System >> Administration I think).  Select all the partitions and choose delete them or just delete one at a time.  This should give you a whole drive of unallocated space with which you can choose to create a new partition of many different formats (ext3, ntfs, etc.)

I'm positive you can do this since I did it earlier today

---

### Post by Merps on 2008-11-16
ok yep I think that the formatting of the new partition is where the disk may be formatted, however, I feel tired when I use Gnome stuff and I often get the urge to buy a VW and drive around in it. 

Perhaps there is an alternative solution to Gparted?

---

### Post by egalvan on 2008-11-16
> **Merps said:**
> I need to wipe the whole Disc, not just rearrage partitions.  Dban works but it takes a minimum of 2 hours +, way too long for me.

Depending on the size of the drive, and how serious you are about "wiping" the drive, then two hours may be short.

You can set DBAN for less-stringent wipe protocols, which will run faster.

But remember that to actually wipe data, every bit on the drive needs to be written... it takes time to write hundreds of gigabytes.

And to wipe it in a manner to foil forensics, the the process needs to be repeated more than once (and the experts disagree on how many).

Sorry, Hollywood has it wrong... the only way to instantly wipe a hard drive is with a 5-pound sledge hammer...real-world wipes take much longer.

And yes, I use DBAN on a  regular basis... been using it for several years to securely wipe hard drives...

---

### Post by Merps on 2008-11-16
> **egalvan said:**
> Depending on the size of the drive, and how serious you are about "wiping" the drive, then two hours may be short.

You can set DBAN for less-stringent wipe protocols, which will run faster.

But remember that to actually wipe data, every bit on the drive needs to be written... it takes time to write hundreds of gigabytes.

And to wipe it in a manner to foil forensics, the the process needs to be repeated more than once (and the experts disagree on how many).

Sorry, Hollywood has it wrong... the only way to instantly wipe a hard drive is with a 5-pound sledge hammer...real-world wipes take much longer.

And yes, I use DBAN on a  regular basis... been using it for several years to securely wipe hard drives...

totally with you DBAN is easy and effective, I hope so anyway, although I not a forensic computer scientist.

but what I was after was a light weight disc formatting utility for when only a light format is required, and even the minimum wipe in Dban is 2 hours, I tried it yesterday.

---

