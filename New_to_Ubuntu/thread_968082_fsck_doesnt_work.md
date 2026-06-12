---
title: "fsck doesnt work"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-11-02
i am on the liveCd and have unmounted all drives and get this message:
fsck 1.40.8 (13-Mar-2008)
why is it not just running?

---

### Post by Paqman on 2008-11-02
What command are you using to run fsck?

---

### Post by stubblepoo on 2008-11-02
litwrrally just:'fsck'

---

### Post by Paqman on 2008-11-03
Ah, well, you'll have to tell it *what* to check. 

Take a look at [this page](https://help.ubuntu.com/community/SystemAdministration/Fsck).

For details about how to use any command, there are manuals available. To read a manual, prefix the command with man. So to get the fsck instructions:
```

man fsck

```
And as always, Google or a search of these forums can be very educational, too.

---

### Post by stubblepoo on 2008-11-03
right, i have tried <fsck -a> and it said checking files and nothing else. i wish to check all files on all partitions and repair everything. can someone please post a complete command for me o monkey like cut and paste into terminal. thank you.

---

### Post by ajgreeny on 2008-11-05
We need to know what your disk setup is first so run ```
sudo fdisk -l
``` in the live CD terminal and post the output of that command back here.  The terminology will very likely be something like ```
sudo fsck /dev/sda#
```with the # being the partition number of your ubuntu install, eg sda2.

---

### Post by stubblepoo on 2008-11-07
sudo fsck /dev/sda3,

now what should i enter,
cheers

---

### Post by ajgreeny on 2008-11-10
I think you now just hit *enter* and wait for a minute or two whilst it checks the system.

---

### Post by stubblepoo on 2008-12-23
now i get the following:
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.41.3 (12-Oct-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda3

---

### Post by unutbu on 2008-12-23
The error message suggests that sda3 is a swap partition. It is unnecessary to do filesystem checks on swap. How about post

```
sudo fdisk -l
```

This will show us your partition table. Then we might be able to suggest the correct command for you. 

What are you trying to achieve/fix?

---

