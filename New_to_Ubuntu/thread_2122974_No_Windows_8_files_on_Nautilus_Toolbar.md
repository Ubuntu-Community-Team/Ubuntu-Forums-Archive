---
title: "No Windows 8 files on Nautilus Toolbar"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by despidey44 on 2013-03-06
I just installed 12.04.1 as a dual boot with win 8 and i cannot find the file partition for my Windows 8 stuff on the toolbar on the left side of the window. What do I do?

---

### Post by Mr. Shannon on 2013-03-06
Run:
```
sudo fdisk -l
```
and
```
df -h
```
and post the results.

Please use code tags when posting the results.

---

### Post by Mark Phelps on 2013-03-07
There are two very different ways to install Ubuntu:
1) From INSIDE Windows, using something called Wubi -- in which the installation is written to a virtual filesystem inside an existing Windows partition
2) Booting from DVD or USB -- in which you create new partitions for Ubuntu and install it there.

Without know which you did, we can't provide detailed instructions.

---

### Post by Lisiano on 2013-03-07
> **Mark Phelps said:**
> There are two very different ways to install Ubuntu:
1) From INSIDE Windows, using something called Wubi -- in which the installation is written to a virtual filesystem inside an existing Windows partition
2) Booting from DVD or USB -- in which you create new partitions for Ubuntu and install it there.

Without know which you did, we can't provide detailed instructions.
AFAIK, it's impossible to currently install Ubuntu using Wubi on Windows 8 due to Secure Boot.
> **despidey44 said:**
> I just installed 12.04.1 as a dual boot with win 8 and i cannot find the file partition for my Windows 8 stuff on the toolbar on the left side of the window. What do I do?
The icons are usually near the bottom, if you can't see them, open a terminal (Ctrl+Alt+T) and do what Mr. Shannon wrote. Please remember to [noparse]```
enclose the text using these tags
```[/noparse]

---

### Post by Cheesemill on 2013-03-07
> **Lisiano said:**
> AFAIK, it's impossible to currently install Ubuntu using Wubi on Windows 8 due to Secure Boot.

Wubi can't handle GPT partitioned disks, which are what you have when you get a computer with Windows 8 pre-installed.
If you install Windows 8 yourself on an msdos partitioned disk then Wubi works just fine.

---

