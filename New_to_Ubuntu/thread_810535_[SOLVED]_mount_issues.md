---
title: "[SOLVED] mount issues"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by vitotol on 2008-05-28
hello guys, after i mount a disk i can find it in /media/
but where is before that?:confused:

---

### Post by sayakb on 2008-05-28
> **vitotol said:**
> but where is before that?:confused:
Not clear. Do you wan't to ask where the media resides before mounting?
Well, linux handles it's devices as folders. So only when you mount, you have a folder. Otherwise, it just has a device link in the /dev/sda or whatever.

---

### Post by vitotol on 2008-05-28
i just wanna know how to mount hda1 from my terminal???

---

### Post by spiderbatdad on 2008-05-28
```
man mount
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by vitotol on 2008-05-28
thank you guys, i also wanna mount my ntfs data partition in the startup...
where do i put this command??????? where is the init? sorry for all these silly questions!:(

---

### Post by spiderbatdad on 2008-05-28
Here's a really good guide:[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sundar261 on 2008-05-28
/etc/fstab

---

### Post by vitotol on 2008-05-28
thanx guys, really helpfull!!!

---

