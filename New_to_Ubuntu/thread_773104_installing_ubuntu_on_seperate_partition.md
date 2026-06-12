---
title: "installing ubuntu on seperate partition"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by littletinman on 2008-04-28
I have three Partitions on my laptop: A 22 gig 64 bit test (for the upcoming ubuntu release; sda4), a 12 gig (32 bit so i can use wifi with my atheros; sda2), and a 64 bit for general use (sda1). There were many problems after the latest hardy upgrade on the third partition (sda1). I've tried to fix them but i think some stuff got messed up earlyer this year when i was working on some other stuff trying to get chipsets to work. 've decided to install Kubuntu onto sda1 and start over for that partition. The thing is, when i install it and i get to the partition editer, how do i tell it to install only on sad1 and use the whole thing. Will it give me an option?

---

### Post by littletinman on 2008-04-28
I'd like to get this done tonight. Anybody out there that can tell me?

---

### Post by zvacet on 2008-04-28
When you come to the partition stage choose manual way and you will see all your partitions.Select sda1 and delete it.On that free space install Kubuntu.

---

### Post by Barrucadu on 2008-04-28
When you get to the partitioning bit, select "Manual". Since you sound familiar with partitioning this should give you no problems.

---

### Post by littletinman on 2008-04-28
Do i have to delete it? Can i just install over it since it is already ext3?

---

### Post by bobplano on 2008-04-28
you should be able to label sda1 as your "/"(root) partition. My recommendation is to back up what information you need that might be somewhere on that drive (just in case), and delete sda1, then start over on that blank space with the new reinstall, marking it as root

---

### Post by littletinman on 2008-04-28
Barr,

  Since i did something similar in the gnome live cd, i'm not too farmilier witht he KDE install process. Is it the same?

---

