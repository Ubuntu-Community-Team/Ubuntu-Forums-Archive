---
title: "Solved"
date: 2019-03-31
forum: New to Ubuntu
---

### Post by aaasixaaa on 2019-03-31
I solved it. Thanks guys.

---

### Post by yancek on 2019-03-31
The first piece of advice would be to post the specific error.
When you say you switched from windows, does that mean you deleted the windows partitions?  Or did you leave windows and install Ubuntu also?
Which windows version do/did you have?
Formatted the drive to what filesystem type?
Have you actually installed Ubuntu and are you able to use it?

---

### Post by aaasixaaa on 2019-03-31
I solve it

---

### Post by oldfred on 2019-03-31
Post these:
lsblk -f
sudo parted -l

---

### Post by mastablasta on 2019-04-01
it could be that the disk is not formatted. check if you can see it in gparted and if you can, try formatting it to a linux file system (such as for example Ext4 - which is the Ubuntu default)

---

