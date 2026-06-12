---
title: "Can't find Install Ubuntu Alongside Windows"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by Sebastian_Agius on 2015-02-11
Hello, I'm a new ubuntu user. Well not actually new since I have not installed it yet. But when installing. I'm having some trouble installing alongside windows.

I followed a tutorial. They do go for something else. But it shows Install alongside Windows BootManager. (I have no idea what it is) I cannot find that or alongside windows and have followed the tutorial all correctly. And on something else. (This was a different tutorial) He has 4 sda folders and one free space for like 40 gb. I have like 9 sda's and like 3 free space that only has like 1 MB or less. Could I please have some help with at least using alongside windows 8/8.1

Thanks in advance. Seb

---

### Post by sandyd on 2015-02-11
> **Sebastian_Agius said:**
> Hello, I'm a new ubuntu user. Well not actually new since I have not installed it yet. But when installing. I'm having some trouble installing alongside windows.

I followed a tutorial. They do go for something else. But it shows Install alongside Windows BootManager. (I have no idea what it is) I cannot find that or alongside windows and have followed the tutorial all correctly. And on something else. (This was a different tutorial) He has 4 sda folders and one free space for like 40 gb. I have like 9 sda's and like 3 free space that only has like 1 MB or less. Could I please have some help with at least using alongside windows 8/8.1

Thanks in advance. Seb

Hi, and welcome to the Ubuntu Forums.

Can you post the output of the following command from a terminal?
You can access the terminal at the Unity Dash (Ubuntu icon on top-left).
```

sudo fdisk -l
sudo parted -l
```

Thanks!

---

### Post by mastablasta on 2015-02-11
or make a screenshot in windows disk manager so we can see how your disk partitions are setup.

---

