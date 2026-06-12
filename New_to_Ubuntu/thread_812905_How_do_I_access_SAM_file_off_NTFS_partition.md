---
title: "How do I access SAM file off NTFS partition?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by achong on 2008-05-30
hey, is there a way to get at the SAM file in my /windows/system32 folder on my ntfs partition through ubuntu?

I have tried mounting the drive, and then looking for it, but the hdd does not show. 

Any ideas anyone?

Cheers

---

### Post by aysiu on 2008-05-30
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

