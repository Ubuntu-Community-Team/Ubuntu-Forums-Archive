---
title: "[SOLVED] Making Ubuntu Partition Bigger"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-06-28
Hi. I want to add more space to my ubuntu partition. From what I heard I should completely format my ubuntu partition and then reinstall. I looked how to backup ubuntu [here]("http://ubuntuforums.org/showthread.php?t=116999"). 
Or, is there a way to add unallocated space to a partition that has already been formed.
What is the best way to go?

---

### Post by ajgreeny on 2008-06-28
Gparted on the live ubuntu CD will do what you want.  You can use it to reduce your windows partition size as well if that's what you want.  How you do it will depend on where on the disk the free space is allocated and whetherv you need to move the ubuntu partition backward on the disk, but all is just about possible.  If it is just a case of adding space to the end of the ubuntu partition, it is very simple, just select the partition and click on "resize" then move the right hand end of the area to the right to the size you want.  There should be np problems doing that, but as always, make sure you have everything backed up before you do it, just in case.

If you need more help, show the output of sudo fdisk -l in terminal, and/or let us see a screen capture of the gparted window, this time using your ubuntu install, showing the partition layout (Alt+Print Screen) and it will make it easier to give you detailed recommendations.  You will not be able to use your installed ubuntu to do the partition work, however, as you can not edit mounted partitions, and of course, if you are using ubuntu, it is mounted.

---

### Post by Promaster91 on 2008-06-30
I was able to use the Gparted CD. I just had to force my video drive. Thanks.

---

