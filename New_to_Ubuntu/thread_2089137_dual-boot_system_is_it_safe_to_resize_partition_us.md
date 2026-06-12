---
title: "dual-boot system: is it safe to resize partition using  windows Disk Management?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by pellefantus on 2012-11-28
Hello,

I have a partition that I resized using gparted from my ubuntu and after that I installed windows 7 on that.

partition 1: ubuntu
partition 2: windows
partition 3: unallocated

-->

partition 1: ubuntu
partition 2: windows (bigger)


Now theres a bit of freespace left and I would like to resize my windows 7 partition to use that free space.

If I partition it from ubuntu with gparted, then windows might protest and I would need to "repair" my win box. 

So is it safe to resize the windows partition with windows disk management from inside windows. I do not want to risk my ubuntu partition at all, and even if I dont touch it they are in the same harddrive.

---

### Post by audiomick on 2012-11-28
> **pellefantus said:**
> So is it safe to resize the windows partition with windows disk management from inside windows. I do not want to risk my ubuntu partition at all, and even if I dont touch it they are in the same harddrive.

Yes, in fact many people suggest not touching windows partitions with gparted.

I believe that gparted will handle windows partitions fine in a lot of cases, and the gparted people do claim that the program will do this. On the other hand, why not use the tools provided by the manufacturer of the product to work on the product?

You might like to de-frag the partition first, then use the windows tool to increase it. Start the machine a couple of times into windows when you are finished to allow windows to run the disk checking utility if it feels it needs to.

It is unlikely that the windows tool will do anything to your Ubuntu partition, as it does not recognise the Linux file systems. I am not sure, but I think it will see the Linux partitions as unformatted partitions. Just look carefully at what you are seeing on the screen and you should not have any problems.

---

### Post by pellefantus on 2012-11-28
> **audiomick said:**
> Yes, in fact many people suggest not touching windows partitions with gparted.

I believe that gparted will handle windows partitions fine in a lot of cases, and the gparted people do claim that the program will do this. On the other hand, why not use the tools provided by the manufacturer of the product to work on the product?

You might like to de-frag the partition first, then use the windows tool to increase it. Start the machine a couple of times into windows when you are finished to allow windows to run the disk checking utility if it feels it needs to.

It is unlikely that the windows tool will do anything to your Ubuntu partition, as it does not recognise the Linux file systems. I am not sure, but I think it will see the Linux partitions as unformatted partitions. Just look carefully at what you are seeing on the screen and you should not have any problems.

Thanks maan
:guitar:


If I dont reply here after tomorrow, then the future reader can assume that everything went fine.

---

### Post by audiomick on 2012-11-28
If it works for you, then please come back and use the thread tools drop down at the top right to mark the thread as solved.

---

