---
title: "Spliting Partition failed"
date: 2017-02-03
forum: New to Ubuntu
---

### Post by alishk on 2017-02-03
Dear All,
Hello
this is Ali. i am new to Ubuntu. i am having a question.
I installed ubutu from usb. it never asked me for partition or anything. it just created a whole partition of 500GB. now i want to split it into 3 partition so i can install vmware. but it is not leting me do this. i trying everything from internet. i tried booting from live ubuntu disk and unmount the drive but still its not letting split the disk. please help. i want to either dual boot ubuntu with windows 10 or want to vmware windows 7.

here is the situation of my current drive.
[https://drive.google.com/open?id=0B7jP9H2BGTo2R09iZHNQVUYtSGM](https://drive.google.com/open?id=0B7jP9H2BGTo2R09iZHNQVUYtSGM)

---

### Post by oldfred on 2017-02-03
You have a standard full drive LVM install.
But LVM is intended for managing the entire drive.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 

Do not know if you can install vmware inside the LVM or not. Do not know either.

But you do not use gparted or standard physical partition tools to manage the LVM. 
But one advantage of LVM is you can redo partitions using LVM tools while still booted in the LVM.

You can only use gparted on unmounted partitions, so have to use separate live installer of gparted live disk. And only for the physical partitions.

---

