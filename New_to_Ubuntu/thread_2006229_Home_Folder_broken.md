---
title: "Home Folder broken?"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by domoappo on 2012-06-18
I can't access any of my files. When I click the home folder button on the left bar on my desktop, it just slowly flashes and nothing happens. I also just found out that my Ubuntu Software Center isn't working either. Someone please help!

---

### Post by tempore on 2012-06-18
Open a terminal, type ```
cd /home
```then type ```
ls -l
``` and post the output

---

### Post by domoappo on 2012-06-18
scott@scott-Vostro-V13:~$ cd /home
scott@scott-Vostro-V13:/home$ ls -l
total 4
drwxr-xr-x 67 scott scott 4096 Jun 18 15:58 scott
scott@scott-Vostro-V13:/home$

---

### Post by tempore on 2012-06-18
If you open a terminal, does ```
nautilus
```
open the file browser?

---

### Post by domoappo on 2012-06-18
scott@scott-Vostro-V13:/home$ nautilus
Maximum number of clients reachedMaximum number of clients reachedCould not parse arguments: Cannot open display:

---

### Post by Immolatus on 2012-06-18
here is a bug report about this that might interest you:


[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/910539](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/910539)

---

### Post by domoappo on 2012-06-19
So what does this mean? Is there a way to fix it?

---

### Post by Immolatus on 2012-06-19
well, heres what I would do. get a fresh copy of the most current Ubuntu and do a fresh install. First you'll want to back up your data. If you don't know how there are many good intro commandline references on the web.
If you can do Ctrl+Alt+F1 and you can navigate in tty1(run level 1 root shell) then you can access and copy your files that way(using fewer clients).

It really looks like you've got a rare and interesting bug there.

If I think of anything better I'll post back.:popcorn:

---

### Post by domoappo on 2012-06-19
I hit ctrl+alt+f1 and it took me to some screen I've never seen before. I tried to get out by hitting ctrl+alt+del and it restarted my computer. Now for some reason home folder and software center are working again? This is weird...

---

### Post by Immolatus on 2012-06-19
trippy.....There are 7 run levels on a Linux system, Ctrl+Alt+F7 will bring you back to the GUI run level. Probably dropping to tty1 cut of some clients or reset a cache somewhere. That is weird.:guitar:

---

### Post by domoappo on 2012-06-19
Anyways, thanks so much for the help!

---

