---
title: "Changing /home Destination Folder"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Headstand on 2008-09-20
Currently, my files and settings are on a separate partition. So I would like to change my home destination folder to my separate partition. Any help?

---

### Post by Locutus_of_Borg on 2008-09-20
mount your other partition
cd to your current home
become root
enter this:
```
find . -depth -print0 | cpio --null --sparse -pvd /location_of_partition/
mv /home/ /home_bak
mkdir /home

```

edit /etc/fstab to mount the other partition at /home
```

/dev/sda6   /home  ext3  defaults,noatime 0 0

```
for example

---

### Post by Headstand on 2008-09-20
Okay, now it says it can't find my /home directory and it wont launch any menu items or programs.

---

