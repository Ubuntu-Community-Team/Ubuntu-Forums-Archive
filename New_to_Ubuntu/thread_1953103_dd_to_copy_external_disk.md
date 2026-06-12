---
title: "dd to copy external disk"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by JodiBosa on 2012-04-05
Hi,

I have an external USB disk that I cannot mount so I would like to backup the data first (before switching to windows and running chkdsk).

1) I was thinking of using 'dd'.  Can I simply write to a large file??

In other words:

```
dd if=/dev/sdc1 of=/root/backup bs=1
```2) If the filesystem isn't mounted - how does 'dd' know where the end of the drive is - or will it copy the ENTIRE drive?

thanks, appreciate the help

---

### Post by kemtnbkr on 2012-04-06
Yes, dd will let you output to one big file.  I don't remember the exact syntax, but if you check the dd manpage there's a way to tell it start/end points... but yes, without specifying the start/end points, dd will copy the entire drive.

---

