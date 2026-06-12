---
title: "[SOLVED] How do I change, dualboot to single boot system?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by germanix on 2008-07-23
I currently have both Windows xp and Ubuntu /Hardy on my laptop,both on the same drive but each in its own partition. Each OS has approx. 35GB of own space.
I would like to de-install xp and then use the free space to keep all of my files.
Unfortunately as one of the dumbest users around, I do not have the foggiest notion as to how one does this.
Anyone out there who could guide me?
thank you

---

### Post by LaRoza on 2008-07-23
Delete the XP partition and remove the entry from Grub.

However, this will result in an odd paritioning scheme.

---

### Post by rockerphil on 2008-07-23
i'd personally just back up all your personal files to CD, get your hands on a copy of the Gparted Live CD, wipe all partitions and start with a clean HDD and then pop in the Ubuntu Live CD and choose "use entire hard drive" so that you don't have a weird partition scheme and the entire hard drive is formatted to ext2/ext3 format which Linux deals with a lot better than NTFS partitions, hope this helps,

Phil

---

### Post by germanix on 2008-07-23
Thank you rockerphil and LaRosa fot your quick response and tips. I am sure this will help me to solve the problem.

---

### Post by sydbat on 2008-07-23
I've been considering this too. However, can you just delete the XP partition and then expand the Ubuntu partition into it? I ask because I have a few partitions on my 250GB drive and do not want to disturb them.

---

### Post by rockerphil on 2008-07-23
yes, it's very possible, and doable, but as said before, you'll wind up with a weird partition scheme, i've seen it done, and done it myself, but like i said, my best suggestion is to back up anything you don't want to lose and reinstall, but yes, you can easily delete the Windows partition with the Gparted Live CD, then simply extend the Linux ext3 partition, hope this information helps,


Phil

---

### Post by sydbat on 2008-07-23
Yes, absolutely. But I'm not sure why you say "weird partition scheme". What do you mean by that exactly? 

If XP is in the first partition and Ubuntu is in the second, wouldn't removing XP and making the partition...wait...as I am typing this, I think I figured it out. Because Ubuntu is currently in the second partition, when removing XP and extending the partition, it remains partition 2...right? Then there is no 1st partition. You're right...that is weird...:lolflag:

---

### Post by rockerphil on 2008-07-23
yes, very much so, that and Linux proportions the system partitions (ext2 ext3 and Swap) in relevence to the entire partition you assign it to, i.e. your "second" partition as you call it, so resizing the partition would make the partition scheme unproportionate

---

