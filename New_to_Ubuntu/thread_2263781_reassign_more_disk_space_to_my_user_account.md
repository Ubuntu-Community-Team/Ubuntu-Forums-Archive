---
title: "reassign more disk space to my user account"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by nikunj2 on 2015-02-03
It seems I have plenty of free space (around 400GB) but my user account is out of space (only 1GB left). Is there anyway I can reassign more disk space to my user account?

---

### Post by slickymaster on 2015-02-03
Hi nikunj2, welcome to the forums.

**First things first, back up anything before doing it.**

After that being done:
[LIST]
[*]Boot to a LiveCD or LiveUSB drive in "Try me" mode.
[*]Load Gparted
[*]Resize your partitions (right click, click resize, follow the instructions).
[*]Click apply and sit back while it does the job.
[*]Reboot, taking out the USB stick or CD when it tells you to.
[/LIST]

---

### Post by philinux on 2015-02-03
> **nikunj2 said:**
> It seems I have plenty of free space (around 400GB) but my user account is out of space (only 1GB left). Is there anyway I can reassign more disk space to my user account?

Let's see what the disk space is like. Run this from a terminal and post back the result.

```
sudo fdisk -l
```

---

### Post by yancek on 2015-02-03
By user space, does that mean you have a separate /home partition?  Or are you talking about the filesystem partitions.  
While you're in the terminal, get the output of:  sudo df -h

---

