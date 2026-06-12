---
title: "help after installing"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by silvio7 on 2015-01-30
I just installed Ubuntu but when I logged in it said No Root file system. 
Then it says Please correct this in the partitioning menu. How do I get to that and fix it?

---

### Post by sandyd on 2015-01-30
> **silvio7 said:**
> I just installed Ubuntu but when I logged in it said No Root file system. 
Then it says Please correct this in the partitioning menu. How do I get to that and fix it?

Hi, and welcome to the forums :)

We will need some additional information to help you with your issue.

[LIST]
[*]Computer Model
[*]Output of ```
sudo fdisk -l
sudo parted -l

``` from a terminal on a livecd. You can access the terminal from the Unity Dash (top left button) -> Terminal
[*]How did you install ubuntu? (Boot from USB/CD, from Windows/etc)
[*]Are there any other OSes on your computer?
[/LIST]

---

### Post by silvio7 on 2015-01-30
Dell dimension 3000 and ndont know what code

---

### Post by yancek on 2015-01-30
I don't know how you would log in if there is no root filesystem.  You created that on a partition during the install.  Use the installation medium you used to install Ubuntu and open a terminal (Hold down the Ctrl+Alt+t keys simultaneously) and type the commands suggested sequentially, then post the output here.  Answer the other questions also so it is easier for someone to help you.

---

### Post by silvio7 on 2015-01-30
Will try to do this week. Snow problems

---

