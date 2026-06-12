---
title: "swap help"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by rom67022 on 2008-05-23
Dear Ubuntu forum,
please help me,
after installing Ubuntu on my machine which now has a dual boot with XPSP2 I lost one of my XP partition by mistake, my mistake, and Ubuntu has dicided to use it as a swap partition, I want it back as I have all my music on that partition, how do I do that?

thanks allot in advance

---

### Post by ASULutzy on 2008-05-23
Short answer, if Ubuntu has been using the partition as swap space, you're boned.

Maybe someone can give better advice, but I think that's the nitty gritty of it

---

### Post by bumanie on 2008-05-23
You will have to try something like testdisk or trinity rescue disk which has an ntfs undelete program on it. Read any documentation first re how to use them.

---

### Post by rom67022 on 2008-05-23
Hi ASULutzy,
and thanks for your reply,
you mean that the data is lost?

---

### Post by soxs on 2008-05-23
Probably, swap gets randomly accessed, unless you have a lot of ram (then it will be never accessed, except for sleep states)
So testdisk should do fine for your task.
Start ubuntu and get it:
```
sudo apt-get install testdisk
```
run it from a terminal:
```
sudo testdisk
```
GL

---

