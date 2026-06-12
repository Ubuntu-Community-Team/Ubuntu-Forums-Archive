---
title: "[SOLVED] Unmounting NTFS"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Sawubona on 2008-06-04
hi,

I have a problem with my system automatically loading an NTFS partition which i don't want loaded. I used NTFS Configuration tool and accidentally selected this partition.

I can only unmount this using:

sudo umount /media/(the drive)

is there anyway to unmount this drive permanently (until required)?

---

### Post by sayakb on 2008-06-04
Edit the /etc/fstab (as superuser) and comment (add a #) or remove the drive's entry.

---

### Post by Sawubona on 2008-06-04
thanks again. worked perfectly. learning something new everyday.

---

### Post by sayakb on 2008-06-04
NP :).. Mark the thread as solved (Thread tools->Mark thread as solved)

---

