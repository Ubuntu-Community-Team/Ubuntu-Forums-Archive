---
title: "[SOLVED] Deleting Backups from Hard Drive"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Lee05162004 on 2008-09-25
Hi, I installed Siimple Backup and set it up to do daily backups to an external hard drive. The problem is that I unplugged that hard drive when I took my laptop to work and it still created the backup, except it created it in a folder named what my external drive is. Now there are more than one backup and I can't seem to delete any of them. By now my hard drive is literally full. How do I change the permissions on the folder so I can remove them? I have tried what I think should have worked but it tells me it can't remove the backups because they are a directory. Thanks for your help.

---

### Post by sisco311 on 2008-09-25
Unplug the hard drive and open your file browser as root to delete the files.
Press Alt+F2 and type:
```
gksu nautilus
```

---

### Post by Lee05162004 on 2008-09-25
> **sisco311 said:**
> Unplug the hard drive and open your file browser as root to delete the files.
Press Alt+F2 and type:
```
gksu nautilus
```

I tried that but I got back an error message it says "Failed to run nautilis as root - Failed to copy the users xauthorization file"

I know I probably need to delete some files to make space and try again, right?

---

### Post by hyper_ch on 2008-09-25
```
sudo rm -Rf FOLDER
```
where FOLDER is the according directory that you want to delete - be careful on that command as you could **easily** wipe everything off your harddisk.

---

### Post by sisco311 on 2008-09-25
try to delete the files from a terminal:
```
sudo rm -rf */media/dir-name*
```
assuming that */media/dir-name* is the path to the directory you want to delete.


NOTE:
first unmount the external drive (if it's mounted)

---

### Post by Lee05162004 on 2008-09-25
> **hyper_ch said:**
> ```
sudo rm -Rf FOLDER
```
where FOLDER is the according directory that you want to delete - be careful on that command as you could **easily** wipe everything off your harddisk.

Thanks, I appreciate it. That worked.

---

