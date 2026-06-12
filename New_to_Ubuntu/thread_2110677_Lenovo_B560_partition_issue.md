---
title: "Lenovo B560 partition issue"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by Liquid Smoke on 2013-01-30
I've got a Lenovo B560 Model 4330 and I'm trying to install ubuntu  beside my Win7 install. I dont want to remove my recovery or Lenovo(D)  however when I shrink my C volume so I can create a seperate partition  for my linux install it says I have reached the maximum amount of  partitions allowed for the hard disk.
 
Is there any way to get around this?
 
Btw from left to right the partitions show as;
 
200MB NTFS No drive letter,
Local disk 254GB NTFS (C),
Lenovo 29GB NTFS (D),
14.75GB No drive letter It also shows up as unused space.
 
I dont want to get rid of my recovery partition. I just need to figure out how to add the partition. Any idea how to do this?

---

### Post by Bashing-om on 2013-01-30
Liquid Smoke; Hi ! Welcome to the forum..

I'll be the one to be the harbinger if ill news.
Under the given prerequisites there is no way to add another partition, the limit is four partitions per disk. Google about to find the technical details. Something will have to give in order to get a partition to install ubuntu onto.

There are ways to arrange this. Has been done many times (delete the recovery partition after copying it to cd is the most prevalent). Search this forum for ideas/instructions/tutorials.


[INDENT]hope to see ya on ubuntu ! 
[/INDENT]

---

### Post by Liquid Smoke on 2013-01-30
What about keeping the recovery partition on a portable hard drive? would that work?

Keeping in mind lenovos one touch recovery system.

---

### Post by Bucky Ball on 2013-01-30
Welcome to the forums. 

You need to delete one of the partitions and create an extended partition in the free space. Inside the extended partition you can then put as many logical drives as you like (theoretically) which sidesteps the four partition limitation.

You essentially will wind up with three primary partitions and an extended partition inside which you can stick as many logical partitions as you like. The extended is like a container for logicals, it is not actually a 'partition' in the regular sense.

Ubuntu will happily exist on a logical drive inside an extended partition; win will not (although you could possibly put the recovery on one, you'd need to further research this).

---

### Post by oldfred on 2013-01-31
You only showed 3 partitions and unallocated space, what is 4th? Often vendors also add a vendor utility partition.

While more on HP issues are the same.
       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

    
Post this to see details of current partitions.

sudo fdisk -lu

---

