---
title: "How to swap Ubuntu from one HDD to another"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by phread59 on 2008-04-24
Any way to port Ubuntu from 1 HDD (80 gig) to a 500 gig HDD and still keep all my settings and lists?  I originally put Ubuntu on a 80 gig hard drive.  I have a new 500 sitting aside that I think I want to put Ubuntu on.  I like Ubuntu so much I want it on a larger hard drive for a pemanent home.  I will then use the 80 to play with 64 bit or other distro's.  I just want a nice safe place for it.  Any suggestions?

Mark Shuman

---

### Post by logos34 on 2008-04-24
Simply copy the entire partition(s) using Gparted (on live cd).
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

Or use dd command.
> 
Copy one hard disk partition to another hard disk:

dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror

sda2, sdb2 are partitions. You want to copy sda2 to sdb2. If sdb2 doesn't exist, dd will start at the beginning of the disk, and create it. Be careful with order of if and of. You can write a blank disk to a good disk if you get confused.
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)


---

