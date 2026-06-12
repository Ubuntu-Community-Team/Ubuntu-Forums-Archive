---
title: "Navidia Drivers"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by F.R Mostert on 2012-11-10
Hi I run Ubuntu 11.10 and have run from root Navidia config now I cannot get into X I can only excess root even in earlier installations.  How can I restore from root to get back and how can I install my navidia drivers.

Dell laptop XPS L502X Geforce 540M graphics card.

Regards

Reimerd:P

---

### Post by HiImTye on 2012-11-10
nvidia-xconfig makes a backup before it saves so you should just be able to put in the old one
```
ls /etc/X11/xorg.*
```and look for the old one then replace the new one with the old one
```
sudo mv /etc/X11/<old_file> /etc/X11/xorg.conf
```

---

### Post by F.R Mostert on 2012-11-10
Hi HiImTye thanks for that but it respond read only system when in root I even tried su but no luck

---

### Post by HiImTye on 2012-11-10
did you log into a recovery console? if so you need to remount the file system rw
```
mount -o remount,rw /
```

---

