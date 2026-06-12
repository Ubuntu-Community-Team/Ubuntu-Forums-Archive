---
title: "bring partitions together"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by ccl4 on 2008-07-10
hello,
i have both ubuntu and windows vista, however i want to bring 2 partitions under windows together (nfts). how can i do best? with gparted? thanks

---

### Post by sydbat on 2008-07-10
Just to clarify, you want to make 2 partitions into 1 partition? You can do it, but everything on both partitions will be destroyed. Make sure you have EVERYTHING on both drives backed up before doing anything.

And, if one of the partitions is the Vista OS, you will loose Vista and have to reinstall that OS.

May I ask why you want to do this?

---

### Post by ccl4 on 2008-07-10
i know, there are nothing in these partitions yet and is not the windows partition. well on of them is a 6gb partition, few capacity, that is why i want to do that.

---

### Post by sydbat on 2008-07-10
OK, if they are empty, it should be straight forward. I think you have to delete them then create one partition. You can use gParted (available in Synaptic or from the Live CD) or go into Windows and use the computer management tools. I'd use gParted.

---

### Post by ccl4 on 2008-07-11
is there a detailed instruction? thanks!

---

### Post by Elfy on 2008-07-11
In gparted you would delete both the partitions and create a new one in the resulting unallocated space.


I fthey are not mounted in ubuntu install gparted and run it from there

```
sudo apt-get install gparted
gksudo gparted
```

Hightlight partitions you want to delete - right click and delete partition, once bothe done, rightclick unallocated space and select new

---

### Post by pjvandehaar on 2008-07-13
I dont know much about this, but im thinking that if you deleted one and moved it next to the other you could just resize the other to fill up the space.
I sure hope so, because I installed ubuntu on 4gb planning to do that as soon as I find a way to defrag my ntfs partition and get another 15-20 gigs of room...
but i could easily be wrong.

---

### Post by kansasnoob on 2008-07-13
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

