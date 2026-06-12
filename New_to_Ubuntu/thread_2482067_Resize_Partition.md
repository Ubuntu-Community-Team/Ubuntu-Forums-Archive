---
title: "Resize Partition"
date: 2022-12-18
forum: New to Ubuntu
---

### Post by pussekatt on 2022-12-18
I have Ubuntu 20.04 on my HDD and I want to shrink the Ubuntu partition but I am not sure what partition it is.I tried using gparted but I dont understand what to do there either.Can someone walk me through how to shrink this partition please.
This is what I have     dev/sda1 System partition
                                   dev/sda2 465 GB
                                   dev/sda3 1mb
I tried to alter dev/sda3 to 50GB but I ended up with only 1mb to
As you can see,I dont need 465 GB so I am trying to make a partition of 50GB to put another OS on.

---

### Post by VMC on 2022-12-18
What's the output of ```
lsblk -f
``` That will give better understanding of partitions.

---

### Post by yancek on 2022-12-18
Boot the system and from a terminal run:  df -h  The partition which shows / under the Mounted on column is your root system partition.
You cannot resize a partition from the system you have booted.  Use a 'live' Linux USB/DVD to do it.  The link below is the online GParted manual which explains resizing partition under the Advanced Partition Actions section. 

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

