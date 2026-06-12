---
title: "Filesystem usage at 100 percent and I can't delete anything"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Alyx_Mazerov on 2014-02-24
Yesterday I reformatted and reinstalled 12.04 on my 500Gb hard drive.  Today I was setting up with programs like Skype, guvcview, Openshot, etc.  It was running slow so I checked my disk usage and it was at 80 percent.  So I started deleting stuff I didn't need but instead of freeing up space it did the opposite.  Now it's at 100 percent and I can't even attempt to remove any programs.  I just get error messages saying I can't do it because I don't have any disk space.

---

### Post by jonedney on 2014-02-24
Hi Alyx,

You should be able to boot off a Live CD, and access the filesystem to remove some things you do not need.

500 GB full already?  Where is it all?  Personal documents/photos/music I assume?

---

### Post by Vladlenin5000 on 2014-02-24
> **jonedney said:**
> 500 GB full already?  Where is it all?  Personal documents/photos/music I assume?

Not necessarily. Often some buggy apps/processes produce "endless" log files.

---

### Post by ibjsb4 on 2014-02-24
Look for large files:

```
sudo find / -name '*' -size +1G
```

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Alyx_Mazerov on 2014-02-24
All my pics, music, movies, etc. are on an external so it can't be that.  The only stuff I have on the internal are programs.  I shut down for the night.  I'm afraid I won't be able to boot tomorrow.

---

### Post by monkeybrain20122 on 2014-02-24
Check the disk usage analyser, you can just type 'disk' in the dash to bring it up.

---

### Post by Impavidus on 2014-02-24
Most likely overflowing log files. If you can't boot, use the live disk, and then check the log files. They are in /var/log/. Make sure you have the log files of the installed Ubuntu, not the live session. If they are very large (gigabytes, they shouldn't be much larger than about a megabyte each), then check for repeating lines. If you post the repeating lines here, we may be able to help.

---

