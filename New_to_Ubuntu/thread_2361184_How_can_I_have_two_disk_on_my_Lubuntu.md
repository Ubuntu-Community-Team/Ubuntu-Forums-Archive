---
title: "How can I have two disk on my Lubuntu?"
date: 2017-05-13
forum: New to Ubuntu
---

### Post by sed_faster on 2017-05-13
Hello folks,

I intend install Lubuntu on pc with two disks. The first disk it is where I will install SO and the another disk where I will use to management my data. How should I configure the system to SO can see the second disk and use it which a simple disk?

I am thinking format all disk as ext4 system file!

Thanks :popcorn:

---

### Post by Impavidus on 2017-05-13
First format both disks, then install Lubuntu to one disk. In the installer, use the option "something else", which means manual partitioning. When you've done that (and it all works), you can modify your /etc/fstab so that the other disk gets mounted automatically where you want it every time you boot.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by milkness on 2017-05-13
Do you want your second disk to be where all your files (documents and stuff) go to? If so then do as Impavidus had said, must make sure you mount your second disk as your home directory (by home directory I mean /home/USER (USER = your user) directory).

---

