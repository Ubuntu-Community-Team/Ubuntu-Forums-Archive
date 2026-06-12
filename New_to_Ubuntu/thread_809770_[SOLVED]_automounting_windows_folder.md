---
title: "[SOLVED] automounting windows folder"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
I want to have my c: (located under /media/PRESARIO), to auto mount when i login to Ubuntu. i know i have to enter a line under fstab, but i don't know what to exactly add. I'm try trial and error, but I'm scared im going to mess something up.

---

### Post by Paqman on 2008-05-27
[Psychocats to the rescue!](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Vicfred on 2008-05-27
This guide works for me =D

[GUIDE]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by adobrakic on 2008-05-27
Paqman, that guide confused the hell out of me. :x The terminology is still very new to me, and if it doens't follow exactly what I have, i get lost easily.

I tried your guide, Vicfred, and this is what i got:
[img]http://img516.imageshack.us/img516/2584/screenshotadoadodesktopth4.png [/img]

at first it says there's an error, but then it says that my drive is mounted. Should i unmount first, then re-do the steps, or did it finish successfully?

---

### Post by adobrakic on 2008-05-27
Sorry, i had bumping threads, but this is really bothering me.

---

### Post by Royke on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=785263]("http://ubuntuforums.org/showthread.php?t=785263")

:lolflag:

---

### Post by Paqman on 2008-05-27
> **adobrakic said:**
> Paqman, that guide confused the hell out of me. :x The terminology is still very new to me, and if it doens't follow exactly what I have, i get lost easily.


Ok, just follow it through step-by-step and tell us where you get stuck. Most of it should just be copy-and-paste.

You said you've already got it mounted to /media/PRESARIO? So you've got a mount point set, you'll be able to skip that step.

OR: Just use the super-easy ntfs-config!

---

### Post by Vicfred on 2008-05-27
hmm sorry I didnt say it before, i use the manual way [link]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c")

if your mounting a ntfs partition you should end adding a line like this to the fstab file

```
/dev/sda1   /media/PRESARIO   ntfs   auto,user,fmask=0111,dmask=0000,nls=utf8   0   0
```

the sda1 may change depending on the output of

```
sudo fdisk -l
```

---

