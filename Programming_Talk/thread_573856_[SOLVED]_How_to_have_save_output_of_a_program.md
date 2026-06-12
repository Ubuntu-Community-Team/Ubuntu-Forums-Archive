---
title: "[SOLVED] How to have save output of a program"
date: 2007-10-12
forum: Programming Talk
---

### Post by jdrodrig on 2007-10-12
Hi,

I write some basic fortran codes for my thesis, and I would like to always save a second copy of the "on-the-screen" output....how can I do it?

I normally either run: a.out
OR
nohup a.out >& a.log &

But the second only saves to a.log without showing anything to the screen...how can I have both? output on the screen and a backup copy to a file?

Of course on my code I have multiple WRITE(xxx,*) to different files unit's xxx, but I would like to save everything that I write to screen too.

Thanks,
D.

Sorry for the obvious typo, I meant "how to have a second output of a program" as title...I guess my eyesight is not what it used to be....

---

### Post by bigboy_pdb on 2007-10-12
You might want to take a look at the following site (specifically "5.2.2.3. Writing to output and files simultaneously"):
[http://linux.die.net/Intro-Linux/sect_05_02.html](http://linux.die.net/Intro-Linux/sect_05_02.html)

---

### Post by jdrodrig on 2007-10-12
Thanks a lot bigboy_pdb, that is exactly what I needed!

Once acain, the usefulness of these forums is proved!

---

### Post by bigboy_pdb on 2007-10-12
You're welcome

---

