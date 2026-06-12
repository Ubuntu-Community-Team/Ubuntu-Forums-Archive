---
title: "[SOLVED] Boot partition filling up"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by chrisod on 2008-08-16
I have a 7 GB boot partition that normally has about 4 GB in it. (Ubuntu 8.04) Home is on a separate partition. My laptop is acting wonky and it appears to be related to the fact that by boot partition is suddenly full. However, in browsing through it, I'm not seeing anything obvious that should not be there. What directories are most likely to be harboring temp files or other things I need to delete? I did have a brutal lockup with Gimp last night that required a push button restart. Maybe a bunch of crap got written to the boot directory when that happened?

I could just make the boot partition bigger but I'm having trouble with that too. When using Gparted via the live CD it keeps remounting that damn partition when I try to resize it, and obviously you can't resize a mounted partition.

Any ideas?

---

### Post by lisati on 2008-08-16
A couple of things come to mine:
[LIST=1]
[*]Empty the trash
[*]enter ```
sudo apt-get clean
``` (and other similar cleanup commands) from the terminal
[/LIST]
These may help free up some space.

---

### Post by dje on 2008-08-16
have a look in Applications >> Accessories >> Disk Usage Analyser and scan the filesystem to see what is using up all your space or you can use this command in the terminal:
```
sudo du -h --max-depth=1 /
```

dje

---

### Post by chrisod on 2008-08-16
sudo apt-get clean bought my 200 MB. It's a start :) It went from 4GB to 7 GB in a week or so, there must be some big honking files there but I just can't find them.

---

### Post by dwhitney67 on 2008-08-16
Surely you mean the "root" partition, not the "boot".  Some people, including myself, have a separate "root" partition from the "boot" partition.  The latter has the linux kernel images and related files, including the menu.lst.

The "root" partition has all of the other system files, including applications, configuration files, etc.  I bet that your linux images are in your root partition, because this is typically how Ubuntu sets things up.

I would look in /tmp to see if you find any file(s) that could be candidates to remove.  That is probably where most "junk" is stored by open-source applications during run-time.

If you have old linux kernels, you could get rid of those too.  But this can be dangerous because if you screw something up, then you won't be able to boot.

P.S.  On my system, 9.1GB of 16GB is used on my root partition.  So your 7.1GB is not that bad.

---

### Post by chrisod on 2008-08-16
I figured it out - but it makes no sense to me. I noticed that the backup files created by Sbackup accounted for the missing 3 GB in my root partition. Here is the weird thing though - the backup files are stored on a NAS drive, so I have no idea why my file system was reporting that they were consuming laptop drive space. When I deleted the backup files from the NAS drive the space came back.

Does that make any sense at all? I've got 50 GB on the NAS drive that doesn't cause any problems, but something apparently isn't working when stored there by Sbackup.

Anyway, I have my root partition back, thanks for the help. Now I need a new backup solution.

Added: In the immortal words of Homer Simpson, DOH! I never added an /etc/fstab entry for the new directory on the NAS drive, so it was writing the files locally and I thought they were on the NAS drive.

---

