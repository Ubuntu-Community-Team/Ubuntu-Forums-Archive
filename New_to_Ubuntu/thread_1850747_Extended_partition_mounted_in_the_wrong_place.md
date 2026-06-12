---
title: "Extended partition mounted in the wrong place?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mars-o on 2011-09-27
Hi,   During fresh installation of ubuntu 11.4 yesterday, i create 3 partitions   
100gb primary-/dev/sda1 (mounted in /home), Ext4   
40gb logical - /dev/sda5 (mounted in /home), Ext4   
20gb swap   but i can't find the 40GB.    

 (i'm already losing disk space since im downloading some torrents)  
  and i think my swap is too big (i just recently, and my swap should be just ~6GB, since my RAM is 3GB.) - pls let me know what should be my swap size, if this is incorrect.thanks    

iwant to unmount, and delete these 40GB, and 20GB partitions, and create again.   
But i have this unmount error: (device is busy)   
[[IMG]http://www.freeimagehosting.net/t/44e94.jpg[/IMG]]("http://www.freeimagehosting.net/44e94")  

 Please advise what i should do,  and where should i mount the partition, so i can use it.    

Thanks!

---

### Post by Leppie on 2011-09-27
You cannot unmount a partition that is in use. In order to modify any of your partitions, you will need to boot off a livecd. You will then be able to use gparted to resize them.

You most probably want a layout like this:
/ : ~15GB
swap : ~4GB
/home : the remainder of the drive

---

### Post by mars-o on 2011-09-27
thanks Leppie. 
i tried gparted, but i cannot unmount th 40Gb.

Does this mean i have to reinstall ubuntu? to fix my partitions? 

when i reinstall, where should i mount the extendend partitions? does it need to be /home?
i'm confused. coz i can't see clearly/use the partitions (unlike windows, where you can see drive C,D,E..., and copy paste files in those drives C,D,E.

(i'm so newbie. :))

thanks.

---

