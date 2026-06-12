---
title: "Unable to access my windows partition?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by wownerd87 on 2008-10-22
Hi guys,
I tried clicking on my Windows partition to explore it for the heck of it a couple days ago and it let me browse through it, today I tried and it wont.It says, **Unable to mount the volume ** Anyone have any idea? Thanks

---

### Post by namegame on 2008-10-22
Did allow your computer to complete a full shutdown process while on your Windows partition?

If not, it will be flagged to Ubuntu as not safe or damaged and it won't mount.

---

### Post by stephanvaningen on 2008-10-22
Two alternatives:
* Re-start to Windows and close properly
* Force it to mount to once mount via command-line:
 ```
sudo mount -f /dev/sdx /media/amountpoint
```

---

### Post by wownerd87 on 2008-10-22
Well, I did get a blue screen and windows shut down before i got on ubuntu, so thats probably it. Thanks

---

### Post by bodhi.zazen on 2008-10-22
Please note that, although rare, forcing a mount can lead to data loss.

---

