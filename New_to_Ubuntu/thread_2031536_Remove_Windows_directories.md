---
title: "Remove Windows directories"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by gaius88 on 2012-07-22
Dear folks,

I have recently installed Ubuntu on my old laptop after having had Windows trouble for the umpteenth time. It's an old laptop and I don't particularly care that the Windows partition is still sitting there. Now I'd like to bluntly rm the WINDOWS/ and the Program Files/ directories as they take up a lot of disk space. My question is: can I safely do that? (of course I had my data backed up first...). And should I update the settings in GRUB before I try this?

I know that this is a pretty brutal way of freeing up space but I would prefer not going through the hassle of repartitioning since it's my old laptop anyway...

Thanks for any feedback!

---

### Post by TheFu on 2012-07-22
If your install was using Wubi, reading this [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) should help you decide. I've never used wubi, so I'm not prepared to say is it ok (though it might be fine).

If your Linux install was to a different partition and you have all the data moved off the Windows partition, delete away. Just be certain you really have all the data and programs you want to retain saved elsewhere.

---

### Post by Austin Texas on 2012-07-22
Assuming that you have the stuff that you want to keep from the Win partition  is  backed up somewhere besides that partition, I think running gparted to format that partition is quicker and easier than deleting directories. 
And you will have a nice clean partition to use for backup or whatever. Right now it is formatted for Win.  You can format for ext2 or ext3 for linux - better file systems. 
ext2 is better for backup partitions. ext3 is better for your OS partition.

---

### Post by NikTh on 2012-07-22
Hi , 
It it important to say ,what install do you have, wubi or regular dual-boot ? 
If you have regular dual-boot then..
...check out this simple GUI program . [_**OS- Uninstaller**_](http://ubuntuforums.org/showthread.php?t=1769489) 

I think it will help you to do your job easily. 

Thanks

---

