---
title: "Removed filesystem, Grub Rescue"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by 29732 on 2011-11-15
So, I had to remove Ubuntu from one of the PCs.
What did I do? Remove the extended partition.
Reboot.
WHOOPS.
Grub rescue, no such partition.
How do I remove GRUB?
 
Edit: [SIZE=4][COLOR=black]**FIXED. **[/COLOR][/SIZE]
[SIZE=2]Thanking Kansasnoob for his post in another thread (not made by me), he said to sudo apt-get install mbr from a live CD, and then sudo install-mbr /dev/sd"X"[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Didn't have to use the Windows recovery CD.[/SIZE]
[SIZE=2]Again, thanks a lot. Same goes for you guys that tried to help me.[/SIZE]

---

### Post by TeoBigusGeekus on 2011-11-15
You need a windows xp or 7 cd/dvd.
With a winxp one, you boot up with it, select repair (R) during installation, and, once in command line, you give
```
fixmbr
```
to fix your master boot record and wipe grub.

---

### Post by 29732 on 2011-11-15
OH THANK GOD.
I have a spare WinXP CD and it should do the trick.
Thanks.

Butjustincase, what if I can't do that?

---

### Post by TeoBigusGeekus on 2011-11-15
> **29732 said:**
> OH THANK GOD.
I have a spare WinXP CD and it should do the trick.
Thanks.

Butjustincase, what if I can't do that?

First things first and positive thinking as well ;)
Try it and we'll see afterwards.

---

### Post by 29732 on 2011-11-17
> **TeoBigusGeekus said:**
> First things first and positive thinking as well ;)
Try it and we'll see afterwards.
 Augh, I typed in my password but it isn't accepting it D:<
There are other machines that are virtually clones of each other, is there a file I can copy and paste into the C: drive?
(The MBR file?)

---

### Post by 29732 on 2011-11-17
Fixed.

---

