---
title: "Ubuntu is crashing quite often"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by jcroblesemanuelli on 2008-08-08
my ubuntu operating system is crashing quite often, does anybody have a systematic approach to troubleshoot it? I know this is a broad questions but as a new user I don't know where to start.

To be more specific I just tried to turn on my machine (i.e. eee pc 900 with ubuntu-eee) and the automatic fsck (file system check) failed and the computer prompted me to do a manual fsck.  

Don't know what to do next.

---

### Post by tarps87 on 2008-08-08
Have you run the manual fsck, you should be able to use ctrl+alt+1
and login using your normal username then try:
```
fsck /dev/hda1
```
this is assuming you hard drive is call hda1
```
fdisk -l
```
will list all the partinions, you are looking for the ext3 formated one.
(If no drives appear you many need to use)
```
fdisk -l
```

I had this problem after the battery dying and by doing the manual
fsck it fixed the problem.
Hope this helps

---

### Post by Crafty Kisses on 2008-08-08
We need system specs. It could be a system resource issue, but I highly doubt it post the following output of
```
top
```
It can also be a HDD issue, so post the following output of ```
sudo fdisk -l
```

---

### Post by ilrudie on 2008-08-08
Whenever you are having trouble its good to check the error logs.  Most everything will be in /var/log/messages.

try

```
tail -100 /var/log/messages
```If you don't see anything you can increase the number to get more of the error log.

---

### Post by Vorian Grey on 2008-08-08
A lot of people have crashing issues with Hardy, it seems. Some solve them and some don't. Good luck.

---

### Post by jcroblesemanuelli on 2008-08-08
> **Codename said:**
> We need system specs. It could be a system resource issue, but I highly doubt it post the following output of
```
top
```
It can also be a HDD issue, so post the following output of ```
sudo fdisk -l
```

Thanks for your help and replies.  I appreciate it. 

```
fdisk -l
``` output:


[HTML]Disk /dev/sda: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef99ef99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1874    15052873+  83  Linux
/dev/sda2            1875        1962      706860    5  Extended
/dev/sda5            1875        1962      706828+  82  Linux swap / Solaris
[/HTML]

I am not sure how to post the "top" output since I can't copy and paste it.

---

### Post by tarps87 on 2008-08-11
Try, if you have not done so already:
```

fsck /dev/sda1

```
It will guide you through the disk check and try to fix any errors with the drive. Make sure you read whats it says.
I hope this helps.

---

