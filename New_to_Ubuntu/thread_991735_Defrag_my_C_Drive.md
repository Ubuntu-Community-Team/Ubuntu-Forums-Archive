---
title: "Defrag my C Drive"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by inearlygaveup on 2008-11-24
I duel boot with ubuntu - can I still defrag my windows drive

---

### Post by nhasian on 2008-11-24
if its NTFS then I would recommend booting into windows to defrag it.  that's the safest thing to do...

---

### Post by stinger30au on 2008-11-24
if you boot in to windows, sure, go for it

i suggust u use jkdefrag, its magic 

[http://www.kessels.biz/JkDefrag/index.html](http://www.kessels.biz/JkDefrag/index.html)

---

### Post by ad_267 on 2008-11-24
Are you using Wubi? If so then I'm not sure. If you have separate partitions then yes, there shouldn't be any problems with that.

---

### Post by swoody on 2008-11-24
As the others have said, as long as you boot into Windows you should be fine. The C drive recogonized by Windows is actually just the partition it's on, not the entire disk, so there should be no problems defragging that by itself :)

---

### Post by inearlygaveup on 2008-11-24
Thanks for all your help "woody" explained the partition, thats what I was worried about 
thanks all

---

### Post by blazemore on 2008-11-24
No way is ntfs write support in Linux stable enough to shift files around like that. You're going to have to boot into Windows (I'm assuming you have Windows, or why would you have NTFS?)

---

### Post by swoody on 2008-11-24
He was asking about his _Windows_ partition, and everyone here recommended him to boot into _Windows_ to defrag...??

---

### Post by halovivek on 2008-11-24
The best thing is boot in windows and defrag from there it self. 
dont try to defrag from linux. i suffered the lost in data and once again i have done installation of windows.

---

### Post by inearlygaveup on 2008-11-24
Thanks blazemore it was windows I was asking about - thanks for your concern

---

### Post by Tom--d on 2008-11-24
I don't think there are many defrag programs for Linux.
No one really needs them so they are not made.

I think you've got the idea of booting into Windows ;)
C:\, E:\ etcetc are just partitions.
In Linux they call them

/dev/sda1 (first partition)
/dev/sda2 (Second and so on).

Another physical HDD would be:
/dev/sdb1
/dev/sdb2

and so on.

---

### Post by ndefontenay on 2008-11-24
How does the defrag works in linux though. 

If not all the partitions, at least the data partition might get crappy after loads of deleting and savings. No?

I've always assumed linux handle that natively which wouldn't require the use of a defrag tool, but is that true?

Sorry if I'm bit off topic but it's still about defrag :x

---

### Post by Tom--d on 2008-11-24
> **ndefontenay said:**
> How does the defrag works in linux though. 

If not all the partitions, at least the data partition might get crappy after loads of deleting and savings. No?

I've always assumed linux handle that natively which wouldn't require the use of a defrag tool, but is that true?

Sorry if I'm bit off topic but it's still about defrag :x

What I've been told is that the ext3 format defrags when it puts files on. Unlike NTFS, it just dumps it on. ext3 sorts it out.

And yes.. ext3 would get fragmented but not as much as NTFS. Just you won't notice.

---

### Post by philinux on 2008-11-24
> **stinger30au said:**
> if you boot in to windows, sure, go for it

i suggust u use jkdefrag, its magic 

[http://www.kessels.biz/JkDefrag/index.html](http://www.kessels.biz/JkDefrag/index.html)

i'll give this a go on my GF's laptop. That vista defrag is a royal pain. No progress info at all.

---

### Post by Walter_Crankite on 2008-11-24
Hi, 

I was told, some time ago on this forum, that EXT3 does not need defragmentation in the way windows does. 

EXT3 and NTFS use a different approach. EXT3 sort of defrags when you put the file on the filesystem. With NTFS you have to do the defrag yourself. 

Just be sure that you have at least 10% of free space for the EXT3.

Br,
Walter

---

