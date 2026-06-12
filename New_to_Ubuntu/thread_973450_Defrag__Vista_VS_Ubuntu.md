---
title: "Defrag : Vista VS Ubuntu"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by kram_italy on 2008-11-06
Well, hello everyone.
I'm really new to Ubuntu (I've been using it for the past two hours), but I already have a problem.
Well actually it isn't a problem yet, it is just a question.
Once upon a time (this morning) I've partitioned my HD in order to install Ubuntu on a separate partition (I have W Vista on the other one).
I use to defrag my HD in order to keep my Pc running quite well, but I have read that defragging Ubuntu partition could cause many problems. 
So here it's the question: when I degrag HD using Vista, I MUST defrag only Vista partition or it doesn't matter whether I defrag both Vista and Ubuntu partitions?
Sorry for such poor English, if you don't get what I say just write to me.
Thanks for any answer.
Mark, the latest Ubunter!

---

### Post by DrMelon on 2008-11-06
Usually the Vista Defragger won't be able to read your Linux partition, so it *should* skip that partition and just defrag itself. But I'm not entirely sure.

---

### Post by bobnutfield on 2008-11-06
DrMelon is correct....Windows (as stock) will not read a Linux partition.  Ubuntu (or any linux) does not need defragging like Windows does becuase of the way it creates file structure.

---

### Post by kram_italy on 2008-11-06
Anyway I will defrag only the Vista partition; thanks to everyone!

---

### Post by Sonic Reducer on 2008-11-07
kram, i would stay away from the ext2 and ext3 drivers for windows for situations just like this. i once lost literally everything on my two drives (i have my home partition on a separate hard drive) fiddling with the drivers. i think what happened was AVG did a scan in Windows XP and fiddled with everything (or at least fiddled with just enough to break it) on the ubuntu-side. i lost all my music, the OS (which of course i just got the way i like it), all my pics, everything.

if you want something to be available on both windows and Ubuntu, make a fat32 partition as a "De-Militarized Zone", or take a look at [Dropbox]("www.getdropbox.com")

---

