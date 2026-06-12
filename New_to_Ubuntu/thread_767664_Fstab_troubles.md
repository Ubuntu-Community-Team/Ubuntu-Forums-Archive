---
title: "Fstab troubles"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by GreenfieldMark on 2008-04-25
Okay, long story short I was trying to get my cd-burner to work with linux by modifying the fstab file. I did a bit of research and thought I knew what I was doing, but the cd-burner still didn't work. Unfortunately I also did a really, really stupid thing and didn't back up the file before I started messing with it. So I tried to revert it back by memory, but now my dvd drive doesn't work. So I need someone who knows what they're doing to take a look at the two lines of the fstab file I edited and see what is wrong with them. 

> /dev/scd0       /media/cdrom0   udf,iso9660,user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660,user,noauto,exec 0       0

Next time, I'll make a backup, I promise.

---

### Post by qpieus on 2008-04-25
take out the comma between iso9660 and user (but make sure there's a space there instead). My cdrom fstab line looks just like yours but minus that comma.```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

---

### Post by GreenfieldMark on 2008-04-25
Thanks, it seems to be working now. Although I still can't use my cd burner, but I can live with that for now.

---

