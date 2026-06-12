---
title: "[SOLVED] Best partitioner????"
date: 2006-08-07
forum: Other OS Talk
---

### Post by rattlerviper on 2006-08-07
Oh I need help!  Tried to install PCLinuxOS, but I needed to rearange partitions...it failed to do so, I just ided up installing it and tried to put Ubuntu dapper on after...Ubuntu won't resize the partitions either(it will resize windows xp partitions for sure).  
Now I just have Ubuntu on the computer, with a main partition of 38.5gb, and a 1.5 gb swap.  What is the best way to resize the partition? 
I know this isn't tecnically the place where this is supposed to be posted, but who better to ask but a group of distro junkies?

---

### Post by GuitarHero on 2006-08-07
Gparted is a great partitioning tool

---

### Post by Stew2 on 2006-08-07
I second that :). Gparted on the ubuntu live CD works great. Pulled me out of  a scrape or two! 

Regards,
Stew2

---

### Post by Luk8 on 2006-08-07
however, Gparted sometimes has some  options grayed out , so it becomes useless at times. From the liveCD I actually installed linHDD (wich uses cfdisk and other tools ) and worked like a charm, and it's quite easy to use:) .

---

### Post by RAV TUX on 2006-08-07
> **Luk8 said:**
> however, Gparted sometimes has some options grayed out , so it becomes useless at times. From the liveCD I actually installed linHDD (wich uses cfdisk and other tools ) and worked like a charm, and it's quite easy to use:) .

I actually prefer cfdisk over other partitioners

---

### Post by cantormath on 2006-08-07
> **Luk8 said:**
> however, Gparted sometimes has some  options grayed out , so it becomes useless at times. From the liveCD I actually installed linHDD (wich uses cfdisk and other tools ) and worked like a charm, and it's quite easy to use:) .

fdisk

---

### Post by rattlerviper on 2006-08-07
I think I'm giving up for the night!  Been using gparted from the live disk with no luck.  It keeps giving me a error telling me to reboot as a part is active...this can cause kernal confusion? I have no idea, it'll probably make more sense after some sleep.

---

### Post by egon spengler on 2006-08-07
I've have lots of hassle with gparted, cfdisk works much better for me

---

### Post by Rumor on 2006-08-07
I've found gparted's LiveCD to be better than using it as part of the Ubuntu 6.06 LiveCD. It now includes fdisk, cfdisk, sfdick and partimage making it (IMO) the most complete partitioning tool available.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by rattlerviper on 2006-08-08
> **Rumor said:**
> I've found gparted's LiveCD to be better than using it as part of the Ubuntu 6.06 LiveCD. It now includes fdisk, cfdisk, sfdick and partimage making it (IMO) the most complete partitioning tool available.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Great disk!  Gparted still didn't want to do it for me, but I was able to use Yozef's suggestion of cfdisk and get it whipped into shape.  All that work to find out what a horrible thing I was trying to do.  PCLinuxOS was great on the live cd, but just didn't work out for me once installed.  I'm going to go post on it right now.

---

### Post by rattlerviper on 2006-08-08
Oops, and thank you every one.  Was just getting ready to go to bed and I felt like I forgot something...It was that.

---

