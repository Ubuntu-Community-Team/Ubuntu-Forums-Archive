---
title: "Problems with External Hard Drive (Formatting, Deleting Partitions and Managing File)"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by kevin9075 on 2013-10-13
I have 1.5 TB WD My Passport External Hard Drive that I've been using to store files for almost two months now.  Everything was going great until like 3 weeks ago, I was copying some big files (10-30 gb) and the first process went through flawlessly but when I went to move another folder into it, the process froze.  I safely removed the hard drive and plugged it back in and tried again, it went through but again when I tried to move another file it froze.  That was back then.  Now, however, I can't do anything with it.  I'm able to sometimes access the folders but going through them will cause it to freeze again.  I tried to delete the main partition and got an error, I tried to format it and got an error as well.  This was done using the Disk Utility because GParted won't start if the hard drive is connected, it stays on the "scanning all devices" unless I remove the drive.

This is my first time posting so I apologize for any mistakes I might have made when making the thread.

---

### Post by whitesmith on 2013-10-13
Hi, **kevin9075**, and welcome! From your description it sounds like you have a bad drive. WD's site has a utility for testing hard drives. That should be your first step. Let us know what WD's utility reports. My experience with WD has not been entirely positive.

---

### Post by kevin9075 on 2013-10-13
I ran the WD Drive Utilities the SMART Status failed, and both the Quick Drive Test and Complete Drive Test get stuck at 0%.  I tried the Drive Erase feature and it just said that the drive is currently in use.

---

### Post by whitesmith on 2013-10-13
Pretty much what I suspected. I hope you have backups for those files! Otherwise there are free, open-source utilities that attempt to recover data on hard drives. Although I'm a strong advocate of FOSS, in this case I recommend spending $89 and investing in version 6 of a product that's been around since...forever. I'm talking about Steve Gibson's excellent SpinRite. It reads and recovers data from just about every filesystem known to man, including Linux. Sorry I can't offer a quick and easy solution.
[edit] If it's any consolation, at least now you know the source of your problem and can proceed accordingly. Good luck!

---

