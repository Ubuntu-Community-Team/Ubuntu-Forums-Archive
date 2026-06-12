---
title: "Expanding Ubuntu Partition"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-07
Hai ,
     I **installed ubuntu 8.04 using wubi** .....when i install i only select **10 GB for the ubuntu **partition..But now i **want to expand it **now.....The partition in XP where i installed has **20 GB more** ....How can i **give that 20 GB from XP to Ubuntu**.......Please reply soon.....My Ubuntu  is filling  too fast ....

---

### Post by forestpixie on 2008-06-07
This apprently worked - [http://ubuntuforums.org/showthread.php?t=816515&highlight=resize](http://ubuntuforums.org/showthread.php?t=816515&highlight=resize)

You can search in the wubi forum - there are more
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by Daveth on 2008-06-07
you do it carefully and do not rush! Have a read of this first- it lays down some useful thoughts on the subject.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by PatrickMoore on 2008-06-07
> **balachandarlinks said:**
> Hai ,
     I **installed ubuntu 8.04 using wubi** .....when i install i only select **10 GB for the ubuntu **partition..But now i **want to expand it **now.....The partition in XP where i installed has **20 GB more** ....How can i **give that 20 GB from XP to Ubuntu**.......Please reply soon.....My Ubuntu  is filling  too fast ....

you are going to have to  boot from your live disk,  once you are loaded up  run gparted and adjust your partition. its really easy

---

### Post by balachandarlinks on 2008-06-07
**How do i run gparted from live cd**....and **give the steps** to follow.....please...

---

### Post by meindian523 on 2008-06-07
any idea?Take out your HDD and smash it to pieces.:lolflag::lolflag:
Be patient dude.Read this [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Paqman on 2008-06-07
Ignore everybody who's telling you to use Gparted. Gparted cannot resize Wubi virtual partitions. For that job you need to install LVPM in Ubuntu.

Go to [this page](http://lubi.sourceforge.net/lvpm.html) and scroll down to where it talks about "Resizing virtual disks using LVPM"

---

### Post by balachandarlinks on 2008-06-07
I m downloading lvpm and will install today to solve my problem...

---

### Post by forestpixie on 2008-06-07
Which is where you would have got to reading my first post.

---

### Post by balachandarlinks on 2008-06-07
Sorry...thank u forestpixie.....
  Jus now i changed my partition and got 7 GB more space.....Thanks u very much and thanks 4 all for giving their tips and time 4 me...:guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by Daveth on 2008-06-13
and thanks for Paqman for correcting our error re gparted and Wubi virtual partitions- always a good place to learn stuff here:)

---

### Post by meindian523 on 2008-06-15
And please mark your thread solved.

---

