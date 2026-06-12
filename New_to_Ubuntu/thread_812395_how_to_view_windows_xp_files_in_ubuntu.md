---
title: "how to view windows xp files in ubuntu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by noobman2 on 2008-05-29
Hi all, im wondering how to view my files from windows xp pro in ubuntu. Could someone please help me out? Thanks :)

---

### Post by unutbu on 2008-05-29
Please post the output to 

```
sudo fdisk -l
```

This will show the partitions on your hard drive(s).
One of those partitions contains your WinXP filesystem. With the info provided by fdisk, we should be able to mount the WinXP filesystem, allowing you to view those files.

---

### Post by snakebitezz on 2009-08-26
ok this would be easier but i installed linux from inside of windows with the 8.1 live cd so it is on the same drive.... ie the /dev/sda3 soo yeah any suggestions would be great

---

### Post by 3rdalbum on 2009-08-26
> **snakebitezz said:**
> ok this would be easier but i installed linux from inside of windows with the 8.1 live cd so it is on the same drive.... ie the /dev/sda3 soo yeah any suggestions would be great

If you used the "Install Inside Windows" option, then the rest of your hard disk is available in /host.

Go to Places > Computer, double-click Filesystem, and it's under "host".

If you had installed Ubuntu as a proper dual-boot system on a different partition, then it would be a different story.

---

### Post by Luca_turicci on 2009-08-26
o_o when I installed Intrepid some time ago my Windows partition was there at "Places" on the menu, only clicked it and it mounted... and when i installed jaunty and karmic it was the same.

---

### Post by mapes12 on 2009-08-26
> **noobman2 said:**
> Hi all, im wondering how to view my files from windows xp pro in ubuntu. Could someone please help me out? Thanks :)
How have you got this configured? Ubu inside windoze via wubi, dual boot alongside windoze or separate Ubu and windoze boxes?

---

### Post by 3rdalbum on 2009-08-26
> **mapes12 said:**
> How have you got this configured? Ubu inside windoze via wubi, dual boot alongside windoze or separate Ubu and windoze boxes?

I don't think the original poster is going to answer - they probably got it working in 2008. I was responding to the poster who bumped the thread.

---

