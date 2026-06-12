---
title: "I messed up, Help Me!"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by wisedrunkard on 2008-09-04
I attempted to extract call of duty 4 (an iso) with the following command:

sudo mount -o loop /home/ryan/Desktop/COD4.iso /home/ryan/Desktop/

Now everything that was on my desktop is gone and replaced with read only files that I can't seem to delete. Is there a way to delete these files and get back everything that was originally there?

Thanks for the help.

---

### Post by bobnutfield on 2008-09-04
Are you able to open a terminal from the desktop?

---

### Post by kalesh7 on 2008-09-04
try
```

sudo umount /home/ryan/Desktop/

```

that should get rid of the real only files on your desktop(and just maybe return your stuff as well, if it doesn't try a restart, or maybe someone else will give some advice).

---

### Post by Nepherte on 2008-09-04
Drives or disks are typically mounted in /media or /mnt. Maybe you could for example mount an iso to /media/iso in the future. You have to create the mount point before you can mount something to it. kalesh7's suggestion should unmount it and that will remove all those read only files from your desktop.

---

