---
title: "Shrinking Vista - Making Ubuntu Home Bigger?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by caliva on 2008-07-01
I installed Hardy Heron 8.0.4 on my Sony Vaio after first installing MS Vista. I used the shrink volume tool in Vista to reduce it to 135 GB and then installed Ubuntu after.

I used GParted to make the partitions:
2GB swap
20GB root ext3
65 GB home ext3

my question is: since I really dont need all this space for Vista after all, can I shrink the space it uses, say down to 40 GB and then resize the "home" ext3 for ubuntu to something bigger like say 120GB? 

What would be the best way of doing this?

(I still need to keep MS around for some odd tasks :( )

---

### Post by kevmitch on 2008-07-01
Of course, you'll want to back up anything really important before you go playing around with partitions.

If vista will let you shrink more, I would stick with using the shrink volume tool for your vista partition to be extremely conservative about it. That being said, the gparted tool that you'll want to use to resize your /home partition does have the ability to resize windows partitions and does it quite well and reliably in my experience. 

The trick is that when you're running Ubuntu, you won't be able to resize your /home partition while it is mounted. The easiest way around this is to run gparted off the Ubuntu live CD.

---

### Post by ibutho on 2008-07-01
I've successfully used [Parted Magic]("http://www.partedmagic.com") to resize a Vista partition to make more room for Linux. The resizing took a while though.

---

### Post by logos34 on 2008-07-01
the problem, though, is how to add the freed space to /home, because if this is the order of the partitions:


vista 
2GB swap
20GB root ext3
65 GB home ext3

vista and home are not contiguous.  So you'll just be left with an empty space between vista and swap.

---

### Post by kevmitch on 2008-07-01
Gparted can handle the non-contiguous case by moving the partitions around. This will definitely add time to the operation, but it can be done. Don't bother moving the swap though (if that's even possible), just delete it and recreate it. There shouldn't be anything irreplaceable there unless you've written a hibernate image to it.

---

### Post by logos34 on 2008-07-01
> **kevmitch said:**
> Gparted can handle the non-contiguous case by moving the partitions around. This will definitely add time to the operation, but it can be done. 

yes, a lot of 'moving around'...home will have to be copied to the freed space, then swap deleted (and recreated elsewhere) and root moved to end of the disk, then home futher expanded to take up remaining space on the right (he said he wants to 'resize the "home" ext3 for ubuntu to something bigger like say 120GB?')

---

### Post by bhadotia on 2008-07-01
As far as I can guess this will take more than 3-4  hours . Although those are figures when it is done on the live CD.  You will have to use live cd I think Coz I don't think the default partition editor in vista supports ext3.
Why you will have to use the live CD is because you can't resize the partitions when they are being used (mounted) except for the swap.

---

### Post by logos34 on 2008-07-01
> **bhadotia said:**
> As far as I can guess this will take more than 3-4  hours

yeah, at least.

It might just be faster making an image of root and home with partimage and then restore them to their new destinations (but you'd need a backup drive to save the images to)

---

### Post by ChameleonDave on 2008-07-01
Depending on how much data is on there, this could take all night.

---

### Post by caliva on 2008-07-01
I figured that this will take all night, but that doesnt bother me quite as much as overlooking something.

I guess in future, a better bet for dual-boot with MS would be to somehow install Windows and /home ext3 side-by-side. 

Gonna try to shuffle them around in the morning.

---

