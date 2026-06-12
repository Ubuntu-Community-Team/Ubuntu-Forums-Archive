---
title: "Easy way to start over with Ubuntu?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Banisher on 2008-05-28
I've had Ubuntu for about 2 months. The guy who gave me the Ubuntu CD (7.10 for 32 bit) told me to play around with it until I got used to it. I took his advice and now it won't start up correctly. I'm curious to know if there is a easy way to just reinstall Ubuntu 7.10 again. I did put in the CD again and tried to reinstall it that way but it was going to make a 3rd partition of my hard drive. ( I already have it in two because I decided to do a dual boot with Vista) I would be thankful for any guidance.

~Banisher

---

### Post by llama320 on 2008-05-28
yeah, you definitely don't want to make a 3rd partition.

I'm not sure if this is where you're going wrong, but when you get into the liveCD there will be an option for "guided" partitioning or "manual" partitioning..You want to choose manual. Once you get there, you'll probably see three partitions: your windows partition (filesystem will be ntfs), your linux partition (ext3), and swap space (vfat, I think). What you want to do is check the "format" box in front of the linux partition and under "mount point" put /

Then just finish the setup and you should have a brand new Ubuntu

Hope that helped, sorry if you already knew that and all :)

---

### Post by Banisher on 2008-05-29
Thank you Llama320 that did the trick.

---

