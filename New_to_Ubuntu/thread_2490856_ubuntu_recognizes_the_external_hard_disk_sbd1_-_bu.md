---
title: "ubuntu recognizes the external hard disk sbd1 - but won't let me see the data"
date: 2023-09-18
forum: New to Ubuntu
---

### Post by davidstiven on 2023-09-18
Good afternoon!

Can you please help me with the following?

I recently started in the world of UBUNTU and I've been doing great until yesterday I tried to open my external hard drive (SAMSUNG) where I manage my work information, when I connect it -ubuntu recognizes it but does not let me open the information, I get the following error

**error mounting /dev/sbd1 at /media/davidstiveb/SAMSUNG:Unknown error when mounting /dev/sdb1**

I have tried to mount it through the terminal but it does not let me mount the external hard disk.

Does anyone know how to fix it?


Note: the other USB drives are recognized without any problem.

thank you very much...

---

### Post by #&amp;thj^% on 2023-09-18
Will you also include:
```
df -hT /dev/sdb1
```

---

### Post by TheFu on 2023-09-18
What file system(s) does that SSD have?  Were they correctly closed before you booted Ubuntu?  MS-Windows8+ doesn't correctly close file systems, unless you've changed some default settings. As we all know, MSFT doesn't think any other OS exists.

Whenever troubleshooting anything in Linux, you need to look at the system logs.  Without that information we'd have to guess 10,000x time what the issue might be. I'm too old to do that.

---

### Post by yancek on 2023-09-19
Had you been able to access this drive previously from Ubuntu without problems?  
Answers to the questions in the above posts will help toward finding a solution.  Improperly unmounting or removing the disk without unmounting or properly ejecting could damage the filesystem.  If you are new to Ubuntu/Linux, I'm guessing the external has a windows filesystem and it was attached to a windows OS.  If that's the case, you need to disable hibernation (at least temporarily in windows) before shutting down windows.  I'm guessing here so best to answer the questions asked above and take a look at your log files.

---

### Post by MAFoElffen on 2023-09-19
TheFu has a very good point... Do you have Windows and was it previously accessed by a Windows OS?

If so, then start up Windows, ensure that "Fast Startup" is disabled. Plug in the drive, if it says it needs to be repaired, let it. Go to the tray in the lower right and dismount the drive, by right-clicking on "Eject Portable Device"... Wait until it says it is safe to remove. Then try it again with Ubuntu.

That may sound "simple". But has happened to users many times here. and is usually overlooked.

Explanation: Windows believes they exist on a machine in a vacuum. It sometimes will leave the filesystem in an "open state."

---

