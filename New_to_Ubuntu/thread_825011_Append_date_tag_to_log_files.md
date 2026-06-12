---
title: "Append date tag to log files"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-10
basically I have a rsync script with something similar to this:


sudo rsync -av --progress --delete --log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log --exclude "/home/your-username/.gvfs" /home /media/HomeBackup

That was an example one. What I want to learn is what these mean:
**--log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log**

I just have a log file that is simply named "logfile.txt so basically it gets overwritten every time. I want to know how these date/time tags work and where I can get a list of them.

Thanks in advance!

---

### Post by Oldsoldier2003 on 2008-06-10
> **abhiroopb said:**
> basically I have a rsync script with something similar to this:


sudo rsync -av --progress --delete --log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log --exclude "/home/your-username/.gvfs" /home /media/HomeBackup

That was an example one. What I want to learn is what these mean:
**--log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log**

I just have a log file that is simply named "logfile.txt so basically it gets overwritten every time. I want to know how these date/time tags work and where I can get a list of them.

Thanks in advance!

have a look at

```
man date
```
there is an explanation of what each does/stands for.

---

### Post by abhiroopb on 2008-06-10
haha thanks a lot! so easy, and here I was searching on google like an idiot :)

---

