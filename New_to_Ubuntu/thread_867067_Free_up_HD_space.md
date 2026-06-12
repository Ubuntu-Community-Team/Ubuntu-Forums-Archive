---
title: "Free up HD space?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Waffle07 on 2008-07-22
Hi guys/gals!!

I'm dual booting Linux and Vista. When I installed Linux I partitioned a huge amount of HD space for it to use (80gbs idk why, I guess I had no idea what I was doing). Anyway I wanted to free up some of that space so I can use it to store mp3 and such on windows. How would i got about doing that?

---

### Post by eragon100 on 2008-07-22
Get the gparted live cd from here: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Boot the computer with the live cd.

You should see an 80 GB ext3 partition, that is the partition you installed linux on. Make it, say 20 GB, smaller. Then merge the free space with the windows partition, which is probably a ntfs partition.

Keep in mind that both of these operations can take quite some time, up to 30 or 40 minutes for each of them, depending on the speed of your computer.

Reboot and you should have more space in windows.

---

### Post by Potatoj316 on 2008-07-22
It might go faster if you defragment your windows partition first.  Even if it dosent make it faster or the sum of that time and the new partitioning time is longer it would still be worth it to defragment.  It puts less strain on your HD and makes read/write faster.  (you can not defrag ext3 filesystems because they dont get fragmented)

---

### Post by Paqman on 2008-07-22
> **eragon100 said:**
> Get the gparted live cd from here: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")


Gparted is actually on the Ubuntu LiveCD these days, so you don't really need to bother downloading and burning the extra Gparted one. Just pop your LiveCD in and go for it.

**Make sure you've backed up before making any changes**, and defrag the pants off your Windows NTFS partition (I like Auslogics Disk Defrag, it's much faster than the default Windows defragger)

---

### Post by Waffle07 on 2008-07-22
> **eragon100 said:**
> Get the gparted live cd from here: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Boot the computer with the live cd.

You should see an 80 GB ext3 partition, that is the partition you installed linux on. Make it, say 20 GB, smaller. Then merge the free space with the windows partition, which is probably a ntfs partition.

Keep in mind that both of these operations can take quite some time, up to 30 or 40 minutes for each of them, depending on the speed of your computer.

Reboot and you should have more space in windows.

OK, I tried making it smaller last night by using that program. It gave me an error though. When I get home I can post the error log it told me to save.

Potato, I'll try that too when I get home from work.

---

### Post by kellemes on 2008-07-22
> **Paqman said:**
> (I like Auslogics Disk Defrag, it's much faster than the default Windows defragger)

Thanks for the tip, pretty cool package.

---

### Post by richiewrt on 2008-07-22
Using the Ubuntu live cd, I believe that you will have to unmount the partitions, so that may be the error you were getting. Also, since you are moving partitions arround, it is a good idea to make sure all your files are backed up somewhere just in case. I have never had a problem with moving partitions, but if something should happen while moving the partition i.e. you loose power or something, you could lose your data.

---

### Post by Waffle07 on 2008-07-22
Thanks for all your help guys!! I got a decent part of my HD back. But now I have 2 separate partitions one is 20gb and the other is 80gb. Is there anyway to combine these two partitions?

---

### Post by richiewrt on 2008-07-23
Do both partitions contain data?

---

### Post by Waffle07 on 2008-07-23
Yes they both have information on them...the one has my MP3s and the other has something on it but I'm not sure what it is.

---

