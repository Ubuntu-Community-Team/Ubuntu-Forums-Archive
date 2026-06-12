---
title: "Dual boot/ os help"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by guamsouljah on 2012-12-13
Hey guys here is my problem. I bought a net book that had windows 7 starter installed. I got pissed off cause your limited in stuff you can do with a starter pack. I was going to throw it away until a buddy said he would fix it. He installed Ubuntu (v10.10). This was about a year ago. the 10.10 version was a bad setup; coundt update etc. Yesterday, successfully installed the latest Ubuntu version myself and want to get rid of the old one in my partition and have the updated version only. How do i do this. Thanks for your help):P

---

### Post by asifnaz on 2012-12-13
Do you still have windows 7..?

---

### Post by guamsouljah on 2012-12-13
no, sorry....i dont even have a disk for it as it only comes from the manufacture ASUS. I have 2 ubuntu OS on my net book.

---

### Post by Elfy on 2012-12-13
You should be able to delete the partition the old one is on from within the existing install.

Running 

```
df -h
```

will show you what's mounted. The partition mounted at / is the install you are running at that time.

```
sudo fdisk -l
```

Will show you what partitions you have - you should be able to see all of them.

If you boot into a livecd/usb you'll be able to remove the old one and expand the remaining partition to use the unused space.

If you aren't sure - post the results of the above commands here, someone will help you.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Mark Phelps on 2012-12-13
> **guamsouljah said:**
> Hey guys here is my problem. I bought a net book that had windows 7 starter installed. I got pissed off cause your limited in stuff you can do with a starter pack. I was going to throw it away until a buddy said he would fix it. He installed Ubuntu (v10.10). This was about a year ago. 
Did your "buddy" install Ubuntu INSIDE Windows, or did he create a partition and install it there? Important because the removal steps are very different for each.

> the 10.10 version was a bad setup; coundt update etc. Some "buddy"!

> Yesterday, successfully installed the latest Ubuntu version myself and want to get rid of the old one in my partition and have the updated version only. How do i do this. Thanks for your help):P
OK, so HOW did you install it?

---

### Post by guamsouljah on 2012-12-13
Hey guys...Just got thru doing solving my issue. I dont know what all that writing is up top but all i did was reinstall the latest ubuntu os like i did earlier. It said it will erase everything and install it. Problem solved.....thanks anyway:lolflag:):P

---

