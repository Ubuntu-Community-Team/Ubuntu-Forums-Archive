---
title: "Need help fixing sloppy HDD"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2008-04-27
I have been experimenting and loading different versions of linux. Now my HD is really messed up. It's a WD 250G 7200.

The first partition is 51.30G with Feisty 7.10 installed and working (/dev/sda1)
Then comes an unallocated 157.23G section
Then comes the last partition (/dev/sda2). Part of sda2 is sda6 where lives Gutsy 8.04 followed by sda7 839MB a Swap partition which goes with Gutsy (I think)
and then sda5 5.79GB which I am pretty sure is the Swap partition for 7.10

What I want to do is enlarge the partition with 8.04 by about 100GB and the problem I'm having with that is that the unallocated section comes right up to it and GParted will not let me move the unallocated section. Same with the swap sections until I can move the partition with 8.04.

Any ideas?
Peter 
[COLOR=Cyan]......maybe none of this is really happening..........[/COLOR]

---

### Post by master5o1 on 2008-04-27
Simple and easy:

I always have a separated home partition so that I can just ~clean install~ Ubuntu on the dist upgrade.
My partition map is as follows:

swap - ~1000MB
/ - 10000MB <= x <= 20000MB
/home - rest of drive.

So, for my 160GB drive I use:
swap - 1000MB
/ - 10000MB
/home - 14900MB
(or there abouts)

---

### Post by kindafunnylookin on 2008-04-28
Bump

---

### Post by lynnevan on 2008-04-28
You only need 1 swap partition/drive since you can't run both distros at the same time, use the same swap partition for both.
Can you send the results of 
sfdisk -l /dev/sda     ??????

---

### Post by kindafunnylookin on 2008-04-28
Thanks for the info on the Swap. Will get rid of the small one, the rest of the problem has been fixed but here is a look at my drive.
```
peter@hardy:~$ sudo sfdisk -l /dev/sda

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  26464   26465- 212580081   83  Linux
/dev/sda2      26465   30400    3936   31615920    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      29645+  30400     756-   6072538+  82  Linux swap / Solaris
/dev/sda6      27222+  29537    2316-  18603207   83  Linux
/dev/sda7      29538+  29644     107-    859446   82  Linux swap / Solaris
/dev/sda8      26465+  27221     757-   6080539+  82  Linux swap / Solaris
peter@hardy:~$ 

```

---

