---
title: "Combine 2 disks into one partition"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by cmo999 on 2013-03-26
Good day!

My linux system has one 500GB drive that is my main boot drive.  The computer also contains 2 160GB Drives, that I would like to combine into 1 320GB partition.

How do I go about doing this?

Please don't tell me that it's a bad idea and I shuoldn't do it.. I am aware of the risks of a Raid 2 setup, and this is what I want because I want to have an extra space for non-essential files that is 320GB.  

Thank you!

---

### Post by Kopkins on 2013-03-26
Why not just mount them both in different locations?
So you have 2 x 160GB
look
You could have one as your main /home folder and the other as a Multimedia folder. 
So, your home would could like:
```

$ ls /home/<user>
  Documents  Downloads  Desktop  builds  scripts MultiMedia

```

But then you could have your other disk mounted at MultiMedia. Which would have videos, pictures, and music.

That way, you run no risks of a RAID 2 setup and all it takes is a simple backup and edit of fstab.

I see no reason that this is not a good alternative. Is there a reason you NEED a 320GB partition?

Kopkins

---

### Post by cmo999 on 2013-03-27
> **Kopkins said:**
> Why not just mount them both in different locations?
So you have 2 x 160GB
look
You could have one as your main /home folder and the other as a Multimedia folder. 
So, your home would could like:
```

$ ls /home/<user>
  Documents  Downloads  Desktop  builds  scripts MultiMedia

```

But then you could have your other disk mounted at MultiMedia. Which would have videos, pictures, and music.

That way, you run no risks of a RAID 2 setup and all it takes is a simple backup and edit of fstab.

I see no reason that this is not a good alternative. Is there a reason you NEED a 320GB partition?

Kopkins


I appreciate what you are saying, Kopkins, and I have considered possibilities like the one you suggest.  I don't want to get into too much detail, but.. the 500GB drive that is my primary partition now, it used to be an extra drive, where I kept certain files, mostly music, .ISO, movies and television programs that I own and want to have both as a backup incase the disks are physically lost or damaged, and to make them easier to access from my network, as I had the whole drive set as a network share.  There is too much information to fit on a 160GB drive, but I could fit it all on a 320GB drive.  I've considerred dichotomizing the information into different drives, I'd just much rather not, I 'd much rather have it the same as when I had the 500GB as the backup drive, one network location where I can easily find anything from any computer, with any operating system that I run (I have a few different ones, WIndows 7, Windows XP, WIndows 8, Mac OS X, and of course Ubuntu.)

I don't feel to inclined to justify myself or explain my reasaons, suffice to say that I would much rather combine the two drives into one logical drive.  Is there a way to do this?
Surely there must be!

THanks for your feedback, and I hope to hear from you again! Hopefully with an acceptance of my resolve, and pointing me in the right direction for how I might accomplish this!

---

### Post by DuckHook on 2013-03-27
You've made yourself very clear. The process you are looking for is called a logical volume (LVM) that spans multiple disks. Instructions are [here]("https://wiki.ubuntu.com/Lvm") and [here]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html").

---

### Post by Kopkins on 2013-03-27
I totally understand, I wasn't trying to put down your proposed method, just suggesting an alternative. But with your specific case in mind it makes sense to use LVM. DuckHook posted above me with some links to Ubuntu LVM tutorials. The [arch wiki](https://wiki.archlinux.org/index.php/LVM) has a lot of information on LVM. 

Best of luck!

Kopkins

---

### Post by Cheesemill on 2013-03-27
+1 for LVM.

It was designed for exactly your type of situation.

One of the best LVM threads I've come across has been on the #! site...
[http://crunchbang.org/forums/viewtopic.php?id=19411](http://crunchbang.org/forums/viewtopic.php?id=19411)

---

### Post by cmo999 on 2013-03-27
Thanks all!

---

