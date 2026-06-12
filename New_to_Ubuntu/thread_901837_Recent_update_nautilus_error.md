---
title: "Recent update nautilus error"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by anderskitson on 2008-08-26
I just did the most recent update this morning that required me to restart. The first thing i noticed was when i use sudo nautilus in terminal i get this
> seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault


I have tried gksu nautilus in alt f2 and terminal no game either. I need to change permissions on files and this is the way I like to do it, anyone else with this problem or a solution?

---

### Post by aysiu on 2008-08-26
Can you try this? ```
sudo apt-get update
sudo apt-get install --reinstall nautilus
gksudo nautilus &
```

---

### Post by anderskitson on 2008-08-27
Still the same thing

---

### Post by aysiu on 2008-08-27
Can you try this, then: ```
sudo aptitude update && sudo aptitude safe-upgrade
``` and then reboot?

---

### Post by mc4man on 2008-08-27
While I'd think over 24 hrs. you'd have have removed any blank media it's worth mentioning. The most common reason for getting a seg fault with gksu(do) nautilus is having unmounted removable media that **can't** be mounted.

The default behavior atm is when you run gksu(do) nautilus any **unmounted removable media** is mounted under root. If it can't be mounted then either nautilus won't open or it seg faults.

The usual suspect is blank cd/dvd media in a drive.

It's also possible that if a usb hdd or flash drive is connected ( but unmounted) and for whatever reason can't be mounted the same will occur.

edit: note that even though partitions on internal drives are listed under 'removable media' the above doesn't apply there, just usb drives

---

### Post by anderskitson on 2008-08-31
I didn't see your post until today because I forgot to subscribe to this, anyways it was a dvd i burned and left in there, I feel so dumb.

---

