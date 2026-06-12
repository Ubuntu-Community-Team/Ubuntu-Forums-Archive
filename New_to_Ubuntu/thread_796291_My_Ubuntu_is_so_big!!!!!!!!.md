---
title: "My Ubuntu is so big!!!!!!!!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tomissi on 2008-05-16
I happily installed Ubuntu and i´m also running widows and the first problem came because lack of disk space, my firefox started working funny and I solved it by making some space on the hard disk, but i will come again cause the partition is 14gb big and the root.disk of my ubuntu weighs 13 of them! 
what is inside that file??
why mine is so big?
what should i do to prevent new crashes?

Thanks in advance for the help.
Cheers from Berlin.
Tomissi.

---

### Post by Joeb454 on 2008-05-16
13GB?

How did you install Ubuntu? Was it through Wubi (i.e. you installed Ubuntu from Windows)

---

### Post by sharks on 2008-05-16
I have alloted 9 gb for ubuntu and it occupied only 24% of disk space. And this will help u:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by philinux on 2008-05-16
Does the 13 include your home directory?

---

### Post by Paqman on 2008-05-16
> **tomissi said:**
> 
what is inside that file??

That's the virtual partition you created using the Wubi installer. Inside it is Ubuntu.

> 
why mine is so big?

What size did you specify during installation? Maybe you've made the virtual partition a little bigger than it should have been.

---

### Post by tomissi on 2008-05-16
> **Paqman said:**
> That's the virtual partition you created using the Wubi installer. Inside it is Ubuntu.


What size did you specify during installation? Maybe you've made the virtual partition a little bigger than it should have been.

I have cleaned my system following the tutorials proposed above, thx a lot!
Now the partition has 7 gigs free, anyway the root.disk is still 13 gb. I will restart on the other os now and will check disk space with the explorer. I understand now,  when the root.disk is 13 gigs that is the total space of the ubuntu partition and it doesn  t mean that its full, right? Im confused, but everything is running ok. 

Thx very much Paqman!!!

---

### Post by Paqman on 2008-05-17
> **tomissi said:**
> I understand now,  when the root.disk is 13 gigs that is the total space of the ubuntu partition and it doesn  t mean that its full, right?

Yep, that's right. When you boot into Ubuntu you should be able to see how much free space you have on the disk. You can see that in the file manager, the system monitor or the disk usage analyser.

---

### Post by quanumphaze on 2008-05-17
If you want to see what is taking up space on your computer you should try the Disk Usage Analyzer (Apps > Accessories)

Handy to see what is taking up space in Windows too.

---

### Post by zvacet on 2008-05-17
```
df -h
```

---

### Post by eriqjaffe on 2008-05-17
> **tomissi said:**
> I understand now,  when the root.disk is 13 gigs that is the total space of the ubuntu partition and it doesn  t mean that its full, right?Correct.  The 13gb is just how much of WIndows' file system is allocated towards the Ubuntu install.

---

