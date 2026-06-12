---
title: "mounting error"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by thomas717 on 2012-02-29
I am running Ubuntu 11.10 from a partitioned external hard disk with Windows 7 on my main PC internal HDD.
When I go into the Home Folder and click on System Reserved, I get the following message:

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

What does this mean and can I do anything about it?

---

### Post by TeoBigusGeekus on 2012-02-29
For starters, post us the contents of your fstab file
```
gedit /etc/fstab
```
Then post us the output of the following commands
```
sudo fdisk -l
```
and 
```
df -hT
```

---

