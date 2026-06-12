---
title: "File Transfer Hangups &amp; crashes"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by franklin_m on 2013-09-20
I'm running 13.04 and really frustrated. I'm trying to do a pretty simple thing, copy files from documents to an exteranal WD USB hard drive. Tried to copy a big directory last night, approx 13K files, 35GB, worked fine until it hit exactly 12,000 files transferred -- then it stopped. Just froze. Let it sit for two hours and no change. File transfer windows won't close fully (still see progress bar overlay on file icon). Other programs won't function or load requiring hard reset with power button.

This morning, just tried transferring 1,296 files for a total of just 1.8 GB. I hung up again, this time after 1126 files and about 768 MB transferred. Tried to call up terminal, window came up but it locked up, could not access.

This is a pretty simple functionality that is not working. Any ideas?

---

### Post by whitesmith on 2013-09-20
> **franklin_m said:**
> Other programs won't function or load requiring hard reset with power button.One possible answer is that you unintentionally corrupted Ubuntu by doing just that. Multi-user operating systems should never be shut down so heavyhandedly. Instead, simultaneously hold down the Alt and SysRq keys while **showly** typing the initialism formed by "Raising Skinny Elephants is Utterly Boring." This will restart the machine properly, without subjecting the OS to possible destruction. Of course, it doesn't solve your current problem, which I leave for others to speculate on. Good luck!

---

### Post by franklin_m on 2013-09-20
Is there a way to rebuild / repair the files most likely to be the cause?

---

### Post by franklin_m on 2013-09-20
One more thing...I don't have a "SysRq" key....

---

### Post by whitesmith on 2013-09-20
SysRq is marked Print Screen on some keyboards. The underlying Linux kernel is active most of the time when your computer is frozen, so the trick I described will allow you to restart without doing any harm. As for rebulding/repairing a (possibly) corrupted system, I will have to leave that for others to comment on. For that to happen, you'll have to give us as much information as you can. The more specific you are, the better an answer you'll get.

---

### Post by nerdtron on 2013-09-21
I find it more comfortable transferring thousands of files using the command line.
Here's the rsync command to copy files and see the progress of each file and monitor if anything stopped. What's great about this is that if you have stopped it halfway, you just run it again and the copy progress will continue from where you stopped it. Saves time and easy to monitor. If it stops on a certain file, you know which file it is. Great!. :guitar:
```
rsync -vrh --progress /pathto/source/folder/ /media/username/yourdestination/folder/
```

---

### Post by Jonathan Precise on 2013-09-21
---OR---

Run
```
fsck
```
on the partition

---

