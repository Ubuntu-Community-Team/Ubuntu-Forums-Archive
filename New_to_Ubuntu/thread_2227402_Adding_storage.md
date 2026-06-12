---
title: "Adding storage"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by Paul_Wike on 2014-06-01
Evening all,

really new to Ubuntu but managed to get the remote viewer working and starting up with the help of everyone here :)

My next question is I have 3 x 1tb drives but only one is being used so wanted to ask how I add the disks to the existing volume. I have watched various YouTube videos and guides but still don't quite get it. 

I have installed gparted as well.

also I don't know if it's possible but could these be in a raid 5 array using software raid? 

Cheers 
paul

---

### Post by whitesmith on 2014-06-01
RAID 5 has such a terrible reputation that a group was started with the appropriate name (Baarf, meaning Ban All Application of RAID Five), see baarf.org. This stuff is demonstrably bad news from an engineering standpoint. Have you considered RAID 10 to gain striping (for speed) and redundancy (for automatic backup)? Give this one lots of thought. One big benefit is that disastrous array failure is virtually impossible.

As for LVM, you might try [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) or [http://archive09.linux.com/feature/142673](http://archive09.linux.com/feature/142673).

Cheers!

---

