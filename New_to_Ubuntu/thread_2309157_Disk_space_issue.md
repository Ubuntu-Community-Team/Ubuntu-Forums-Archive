---
title: "Disk space issue"
date: 2016-01-08
forum: New to Ubuntu
---

### Post by aaron27 on 2016-01-08
I am running Linux Ubuntu 12.04 server 64bit, we use the machine solely to run Groundworks monitor.

For the last few weeks we have been getting notifications saying our disk is 99% full, however I have run Bleachbit (as root) and I have also used  synaptic package manager then i checked disk space analysis and that says we have alot of free space. Apart from switching off the notifications is there any other way i can reduce the amount of space used on this server?

---

### Post by yancek on 2016-01-08
Use the df -h command to show free space and used space on any mounted partition.  Use GParted also which will show all partitions.  Do you have a separate boot partition?  What do you consider a "lot" of free space?

---

### Post by matt_symes on 2016-01-08
Hi

As yancek suggested, open a terminal and type in the two commands below.

```
df -h
df -i
```

Copy and paste the output from the terminal into your next post.

It will show the amount of free space and the amount of free inodes on your system.

We can then look at maybe removing some old kernels and kernel headers depending on where the problem may lie.

Kind regards

---

### Post by gordintoronto on 2016-01-08
Use synaptic to clean out most of your old kernels, then run: sudo update-grub

---

