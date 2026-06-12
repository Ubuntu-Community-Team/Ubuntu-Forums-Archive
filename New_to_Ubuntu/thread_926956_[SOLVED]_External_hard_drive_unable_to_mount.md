---
title: "[SOLVED] External hard drive unable to mount"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by keefy777 on 2008-09-22
I recently removed my hard drive from ubuntu to transfer some stuff to my kids pc which is windows 
However on trying to put it back on to my ubutu system it says that it cannot mount the drive as it was not removed from windows cleanly (  i did )
and now i cannot mount it at all
Any ideas.

---

### Post by halitech on 2008-09-22
open a terminal and type in
```
sudo mount /dev/sdb1 /media/drive_win -o force
```

changing /dev/sdb1 and /media/drive_win to the location of the external drive and the proper mount pount

---

### Post by timcredible on 2008-09-22
you can also run a check on the drive to see if there are errors.  install ntfsprogs from synaptic and then run ntfsfix on it.

---

### Post by keefy777 on 2008-09-22
Ok i edited etc/fstab but it now says that i am not privileged to mount this volume

---

### Post by bigken on 2008-09-22
> **keefy777 said:**
> Ok i edited etc/fstab but it now says that i am not privileged to mount this volume


did you use **sudo **

---

### Post by keefy777 on 2008-09-22
Ok i did sudo gedit /etc/fstab

And the added this line
/dev/sdb1       /media/disk     ntfs-3g force                    0       0

what do ya reckon

---

### Post by vanadium on 2008-09-22
The only proper solution, at least if you care for the data on the disk, is to have it checked and repaired under MS Windows. There is a reason why Ubuntu won't mount an "unclean" ntfs volume.

---

### Post by keefy777 on 2008-09-22
Ok so if i put it back to the windows system and remove it cleanly again should this solve the problem

---

### Post by bigken on 2008-09-22
yes if its ntfs do a clean shutdown in windows in ubuntu install ntfs  Configuration Tool and you should be ok

---

### Post by keefy777 on 2008-09-22
Thanks that sorted it another good reason not to bother with windows

---

