---
title: "Resising Windows Vista Partitions on Dual Boot"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rstritmatter on 2008-06-09
Hi folks,

Here is a conundrum for the more experienced. I have a functional dual boot, Vista and Hardy, originally created using EasyBCD from within Vista (upgrade on top of windows). Due to not understanding partitions very well and not carefully projecting my needs, I currently have way too much of my 200G sata drive apportioned to Ubuntu and not nearly enough to Vista, which has two partitions, 26.4 system and programs (with only 2.38 Gigs free) and 5.22 data (with only 89 MB free).  For some reason data drive reads as C and system as H-- not sure how this happened, but it is so.  I'm currently in Vista so I can't describe the partition system as linux sees it (but I will provide this if it is needed to diagnose solution).

My problem is: How to reapportion some of my very sparsely used 170G of Ubuntu disk space to those two Vista partitions without doing anything stupider than I've already done :popcorn:.

Your help is very much appreciated. I'm learning, but still a blushing Noob.

:guitar:

---

### Post by cdtech on 2008-06-09
Best to use the live cd gparted. I used it to size my vist and ubuntu. It takes some time to do but works very well.

---

### Post by rstritmatter on 2008-06-09
> **cdtech said:**
> Best to use the live cd gparted. I used it to size my vist and ubuntu. It takes some time to do but works very well.

Thanks.  Isn't the live cd of gparted supposed to run off the cd on startup with "run off cd" enabled?  I thought that I had it working that way, but now it seems that when I try that I go directly into Grub.  Perhaps I need to reburn it?  

Any clues?

---

### Post by JoshuaRL on 2008-06-09
Actually, you should try to do it first through Vista.  Not always, but if you don't do it that way it sometimes messes stuff up in Vista.  Just something to keep in mind.

---

### Post by rstritmatter on 2008-06-09
> **JoshuaRL said:**
> Actually, you should try to do it first through Vista.  Not always, but if you don't do it that way it sometimes messes stuff up in Vista.  Just something to keep in mind.

Ok, thanks. Since I'm having troubles with gparted, I may well give that a try.

---

### Post by rstritmatter on 2008-06-09
I haven't done anything that I can imagine would do this. I've just been installing a few updates in Hardy Heron, and suddenly when I reboot I no longer have Vista Longhorn as an option in Grub.

:confused:

Anyone have a clue as to why this might be, and what I can do to fix it?

Thanks in advance for your assistance!

---

