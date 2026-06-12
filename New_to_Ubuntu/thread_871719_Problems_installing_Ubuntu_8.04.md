---
title: "Problems installing Ubuntu 8.04"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by rcr484 on 2008-07-27
Hi all,

I'm quite new in this and I really want to get Ubuntu installed on my laptop (Intel Celeron M 1,73 ghz, 512 mb ram and Windows Vista Home Basic already installed).

I've burned Ubuntu to a CD, and it works fine on my normal pc, but when I try to run the installer on my laptop, it went wrong.

When I'm booting from the CD, I get the boot menu and I choose that I want to install it. Then I get the boot loading screen. When the bar is full, the only thing I get is a white screen with black stripes.

I'm really lost in this and don't know what it is.

Hopefully someone knows the answer.

Already thanks!

---

### Post by Der Alte on 2008-07-27
Have you tried booting the LiveCD on your laptop and running the graphical installer from there?

---

### Post by arvind5589 on 2008-07-27
no

---

### Post by Bucky Ball on 2008-07-27
When you boot from the Ubuntu installer cd, there is an option below 'Install Ubuntu';

'Check disk for defects'

Did you run that before installing? So many people don't. I suggest you boot up again and run that first. If the disk is corrupt that is your problem right there (possibly). May as well start at the beginning. Good luck ... :)

---

### Post by Ryadt on 2008-07-27
You will have to use the alternate cd to install. Download it from the Ubuntu hompage.:)

---

### Post by rcr484 on 2008-07-27
Yes, I've done that. I'm the installer now in safe mode, and I already made a partition at my harddisk, did that already in Windows. I'm now at step 4, and I'm selecting the right partition. Then I click at next, but then I'm getting the message which says that I didn't defined the root system file. I went back, but I don't know what to do now.

@Ryadt: I'm giving that a try. ;)

---

### Post by Ryadt on 2008-07-27
Select the partition you want to install on which will allow you to edit the partition. In Mount point, select 'root file system'.

---

### Post by Troll_the_Great on 2008-07-27
> **Ryadt said:**
> Select the partition you want to install on which will allow you to edit the partition. In Mount point, select 'root file system'.

Root looks like "/"

---

### Post by rcr484 on 2008-07-27
Jup, thanks guys! It's working. ;)

---

### Post by momoddy on 2008-07-27
hi i'm trying to install debian gnu/linux from [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/) as i don't have a cd/dvd drive right now but the installer does not detect my modem, any ideas?

---

### Post by gjoellee on 2008-07-27
This happened with me...just it was no laptop, check if you are running your screen in Analog or Digital... I needed to make it run digital on the CD, and when not Analog...

---

### Post by halitech on 2008-07-27
try this from a terminal
```
lspci
```

do you know if its a hardware modem or a software modem?

---

