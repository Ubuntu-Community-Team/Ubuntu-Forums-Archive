---
title: "I have to make partition  from windows merged into Ubuntu"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by karthikindraganti on 2015-02-08
Guys Actually I performed a dual boot on preinstalled windows8 system however  I Installed ubuntu in it now Ubuntu has 100 gb in my pc now I want to allot 100 more Gb to it so I formatted a 100gb drive partition and trying to add it is there any possibility guys please suggest me, Your suggestions are welcome and Always valuable

---

### Post by yancek on 2015-02-08
I'm not sure what you want.  You've already created and formatted the partition if you are referring to sda13, the 100GB partition.  Do you just want to use it as data?  You just need to create a mount point for it and put an entry in the /etc/fstab directory.  If it's something else you want, you need to be more clear about it.

---

### Post by Impavidus on 2015-02-09
If you want to use it as some kind of data partition, just do as yancek suggests. The other logical option I see is adding this space to your /home partition (sda8). This however is not so easy, as the root partition is inbetween. It would involve shrinking sda13 to something decent for a root partition, cloning sda7 to sda13, deleting the old root partition and expanding sda8 to the left. You would have to do it from a live disk. Reinstalling might be easier.

I see you have a separate /usr partition. Any particular reason for that or just for fun? It's a bit tight, although workable. I have 7.3GB in my /usr (not including my /usr/local, which is on a separate partition, rather big (automatically gathering data) and more or less portable to a new Ubuntu release).

---

### Post by karthikindraganti on 2015-02-11
Thanks

Thanks YEs it is better Reinstalling ubuntu

---

