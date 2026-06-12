---
title: "[SOLVED] How to make partitions at HD number 2"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by swotie on 2008-04-28
I have 2 HD at 80 GB each ... When I install Ubuntu, I make a swap drive, a root dríve and a home drive at HD 1 ... This is OK

BUT .. then I make a partitions at HD 2 ... I don't know which mount point I must use ...  exsample ... If I use /usr, I have my HD 2 in Home/usr ... I would like to have a drive number 2 ... hvich mountpoint must I use to get that.

---

### Post by hyper_ch on 2008-04-28
I don't understand what you're trying to do :( can you say differently?

---

### Post by swotie on 2008-04-28
If I make a mountpoint at HD2 exsample /usr ... I must go to /home/usr to find HD2 ... I would like 2 have standalone drive ... exsample sdb5 so I can go direct to HD 2 ... hope You understand this

---

### Post by meindian523 on 2008-04-28
If I understand you,you are trying to make additional partitions(what you call drives) on your HDD2.You have already made 3 partitions on HDD1,which are mounted at /,/home and swap respectively,correct?

EDIT:You mean you find your files which should have been in /usr in /home/usr,do you?

---

### Post by swotie on 2008-04-28
Yes

---

### Post by hyper_ch on 2008-04-28
you will have to do manual partitioning and there you can say that your second harddrive (e.g. /dev/sdb1) should be mounted to /usr

But may I ask, why do you want a whole harddrive to mount as /usr?

---

### Post by mlentink on 2008-04-28
If I understand you correctly, at partition time you do not have to select a mount point at all. Simply make the partitions and have GParted format them to ext3 or even ntfs or fat if you want. Those partitions will then be mounted under /media as usual. If you want you can give your partitions labels like disk2, disk3, disk4 or whatever you want.

---

### Post by meindian523 on 2008-04-28
Try opening /usr and check whether it's a simple duplication of files.And if it's not duplication,try hyper_ch's suggestion.

---

### Post by travismoore on 2008-04-28
I don't quite understand you but i will explain how my hard drives are set up and hopefully this will help with yours.

what you need to have usually is swap, root(/) and home where your documents are (/home).

So on my system i dual boot Linux and windows and this is how mien is partitioned out:

**80GB HDD:**
2GB Swap
40GB / (root) file system= EXT3
40GB NTFS (windows)

**500GB HDD:**
40GB /home (home i.e your documents) file system= EXT3
Remaining space is NTFS for file storage

I hope this helps you understand how it works and i hope it is actually the answer you needed.

---

### Post by swotie on 2008-04-28
This is the problem ... I DON'T want to make it as /usr .... I only want a normally drive number 2, there I can store some files ... but then I make a new partitions at HDD 2, I must make a mount point to continue :-(

---

### Post by hyper_ch on 2008-04-28
are you installign now? If so, make screenshots and post them... I have no clue where you are or what you're trying to do.

---

### Post by meindian523 on 2008-04-28
I got it.

swotie:
Make a partition taking up your entire HDD2.Format it to ext3,fat,whatever.In the mount point space,just put something like /media/hdd2(or whatever you want).

---

### Post by mlentink on 2008-04-28
> **meindian523 said:**
> swotie:
Make a partition taking up your entire HDD2.Format it to ext3,fat,whatever.In the mount point space,just put something like /media/hdd2(or whatever you want).

+1 With the following additions:
You do not have to limit yourself to just on partition

In linux, everything is a file, including partitions. This is why they have to show up somewhere in your filesystem, and why they will have to have a mount point. As an example, attach a USB harddrive to your system (or even a USB-stick). You will see them show up in /media.

---

### Post by swotie on 2008-04-28
YES .. it works :-)... I didn't  know I could write something by myself :-(

---

### Post by meindian523 on 2008-04-28
Well,you learnt that today.Please mark this thread solved.:)

---

### Post by swotie on 2008-04-28
But I can mark tis tread as solved ... the function is gone in tread tools :-(

---

### Post by meindian523 on 2008-04-28
Looks like it will have to wait till the forum upgrade is complete.:)

---

### Post by swotie on 2008-04-28
A new problem :-( ... I have made the partition at HDD 2 ... but I can't write to it :-( ... I have no permission

---

### Post by Gregory_NZL on 2008-04-28
> **swotie said:**
> A new problem :-( ... I have made the partition at HDD 2 ... but I can't write to it :-( ... I have no permission

I have the same problem, at install time I mounted a partition as /data and only root has permission to access it. Can anyone advise what I have done wrong?

---

### Post by meindian523 on 2008-04-29
add "user" to your /etc/fstab.eg:If your partition of HDD2 is /dev/hdb1,then it might be looking like this right now in your /etc/fstab

```
/dev/hda9 /media/recovered_disk vfat defaults,auto 0 2
```

Change it to:

```
/dev/hda9 /media/recovered_disk vfat defaults,**user**,auto 0 2
```

---

