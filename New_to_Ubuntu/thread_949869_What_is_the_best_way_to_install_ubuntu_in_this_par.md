---
title: "What is the best way to install ubuntu in this particular situation ?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by quecoder on 2008-10-16
Hello , 
I want to install ubuntu beside windows , my hard disk is divided as follows :
```
                C:         D:        E:        F:        G:        
Capacity:      14  GB    15.3 GB   26  GB    9.5 GB    9.7 GB
Free Space:    1.6 GB    1.7  GB   4.3 GB    7.7 GB    1.9 GB
-------------------------------------------------------------
                                               TOTAL : 75  GB 
```

I want to have a shared partition between windows and ubuntu ( will be exp3 and I'll use FS-Drive as recommended by [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) from windows) as a separate /home partition (will that work?) .. Now the questions are:

1- how to make that shared partition from the previous partitions ( D,E,F,G ) ?

2- should I do this step from windows or via GParted when using the LIVE CD to install ubuntu?

3- if I needed to re-install windows  ( which is located in drive C ) what do I need to do in order to return the boot loader at the beginning back to let me chose what OS to run ?

4- if I wanted to uninstall ubuntu what should I do ?


Sorry for all these questions , but I really want to make sure that I will not mess any thing up and to keep my data safe

---

### Post by Victormd on 2008-10-16
> **quecoder said:**
> 1- how to make that shared partition from the previous partitions ( D,E,F,G ) ?

2- should I do this step from windows or via GParted when using the LIVE CD to install ubuntu?

If you already have the partitions and they're the size you want, you can set them up during the Ubuntu install. A partition manager will come up and you can set them up there using the "Manual" option.

However, I would resize them so you have:
```
                C:         D:        E:        F:        G:        
Capacity:      14  GB    15.3 GB   26  GB    18.5 GB    0.7 GB
-------------------------------------------------------------
                                               TOTAL : 75  GB
```

I wouldn't create a separate Home partition (my personal preference) I would install everything in F and use G for swap (512MB - 2GB). Since Ubuntu has good NTFS support, I would use E or D as your shared partition and if you want to access your HOME from Windows, use FS-drive.

If you're using vista, then you will need to use the Vista partition manager to change the partitions. If your using XP, then you can use GParted to resize them.

**[COLOR="Red"]REMEMBER TO BACKUP ALL YOUR DATA BEFORE STARTING[/COLOR]**

---

### Post by louieb on 2008-10-16
Do you have the Ubuntu live CD?  Can you accees the net with it.
If so I'd like to have a look at the partition table.  
open applications>accessories>terminal
```
sudo fdisk -l
```
 lowercase L at the end.

If you would like to post a graphical view you can open System>Admistration>Partition Editor.  
and press Alt+PrintScreen. that will allow you to save a picture of just the GParted window.

Before giving any partition suggestions it would be helpful to know the partition type (primary,extended,logical) and how Linux name them. (that will be something like /dev/sda1, /dev/sda2 ...

---

### Post by quecoder on 2008-10-16
Thank you for your reply.
But can I make the shared partition after the ubuntu one ( windows -> ubuntu -> shared ) so it's not in the middle as the page i pasted recommended ? or in other words , the partition posistions don't have any effect ?

---

### Post by quecoder on 2008-10-16
Thank you louieb for you reply , I will try to make it now , and will back again

---

### Post by bodhi.zazen on 2008-10-16
I would advise you also learn how Linux refers to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

This is IMO critical to prevent installing or formatting into the wrong partition.

---

### Post by quecoder on 2008-10-16
I tried to make a screenshot as you advised but it doesn't want to be saved when I save it ... 

Here it is when using fdisk -l :
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9141891f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1816    14586988+   7  HPFS/NTFS
/dev/sda2            1817        9729    63561172+   f  W95 Ext'd (LBA)
/dev/sda5            1817        3812    16032838+   7  HPFS/NTFS
/dev/sda6            3813        7208    27278338+   7  HPFS/NTFS
/dev/sda7            7209        8452     9992398+   7  HPFS/NTFS
/dev/sda8            8453        9729    10257471    7  HPFS/NTFS

```

---

### Post by quecoder on 2008-10-16
> **bodhi.zazen said:**
> I would advise you also learn how Linux refers to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

This is IMO critical to prevent installing or formatting into the wrong partition.

Thanks alot , great guide

---

### Post by quecoder on 2008-10-16
**louieb where are you ,,  any ideas ?**

---

### Post by louieb on 2008-10-16
The 1st (/dev/sda1) That is probably your widows install at 14GB thats about right for XP but small for Vista. It is real low on free space  If you have any data you can move off of it I would do that.   I like to keep my partitions below 80% full that one is over 90%.        

The  2nd (dev/sda2) that is an extended (container)  partition. It doesn't hold any data it holds other partitions.  (type logical).  It occupies the rest of the drive. I would not change that.   

The rest of your partitions are logical.  GParted can and probably is the easiest way to resize, delete, create  them if needed.   

Over all your running pretty low on free space (time for a 2nd hard drive maybe).    By the time you get the 5-10GB Ubuntu will need that drive will be pretty full and performance will suffer.    

Do take a look bodhi.zazen's link.  Good Luck

---

### Post by quecoder on 2008-10-16
> **louieb said:**
> The 1st (/dev/sda1) That is probably your widows install at 14GB thats about right for XP but small for Vista. It is real low on free space  If you have any data you can move off of it I would do that.   I like to keep my partitions below 80% full that one is over 90%.        

The  2nd (dev/sda2) that is an extended (container)  partition. It doesn't hold any data it holds other partitions.  (type logical).  It occupies the rest of the drive. I would not change that.   

The rest of your partitions are logical.  GParted can and probably is the easiest way to resize, delete, create  them if needed.   

Over all your running pretty low on free space (time for a 2nd hard drive maybe).    By the time you get the 5-10GB Ubuntu will need that drive will be pretty full and performance will suffer.    

Do take a look bodhi.zazen's link.  Good Luck

can not attach another hard disk atleast now , i'm using a laptop :(
I can resize some drives and form a big one out of them ... but what extension it will have? and will be primary or extended

---

### Post by quecoder on 2008-10-16
there is a small problem ... sda5,sda7,sda8 have a small key beside them and can not be resized from GParted ... but sda6 can ... why that ?

it tells me that they are mounted .. what does that mean?

---

### Post by bodhi.zazen on 2008-10-16
> **quecoder said:**
> there is a small problem ... sda5,sda7,sda8 have a small key beside them and can not be resized from GParted ... but sda6 can ... why that ?

it tells me that they are mounted .. what does that mean?

The most common reason for this is that the partitions are mounted. You have to unmount them ;)

---

### Post by quecoder on 2008-10-16
thank you bodhi

---

### Post by louieb on 2008-10-16
> **quecoder said:**
> ...i'm using a laptop :(
I can resize some drives and form a big one out of them ... but what extension it will have? and will be primary or extended

sda1 is a primary partition.  
sda2 is an extended partition.
sda5,6,7,8 are all logical.  
extension is not the right word.  
A partition has a type of (primary extended or logical) 
and a partition is formated with some file system (ie: NTFS, ext3, fat32 and a bunch of others)

But when GParted asks for type you should be working with **logical partitions.**

As far as the lock being by them. You were probably looking at them with the file browser and as bodhi.zazen said Linux mounts them. So you need close the file browser and right click on the partition and choose unmount.    
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

