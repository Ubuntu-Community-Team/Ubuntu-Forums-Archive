---
title: "Mounting partitions"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by SigmaHog on 2008-04-23
How do I mount my partitions so I can exchange data between them?
I currently have Windows with a ntfs and Ubuntu with ext3, i also know i need something in windows to read the ext3 data... your help is appreciated!!!

---

### Post by tamoneya on 2008-04-23
fs-drivers works pretty well
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by SOULRiDER on 2008-04-23
> **tamoneya said:**
> fs-drivers works pretty well
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Ive used them before and they work great. HOWEVER, remember that if you happen to get a virus, it will be able to affect your linux files, NOT INFECT you linux system, but it may damage or delete stuff on your linux partition.

---

### Post by SigmaHog on 2008-04-23
I rebooted my system now it's telling me to format the partition linux is on and won't let me access my files. what do i do?

---

### Post by Can+~ on 2008-04-23
> How do I mount my partitions so I can exchange data between them?

I answered a similar thread:

For a full list of currently plugged hard disks:
```
sudo fdisk -l
```

To mount a hard disk
```
sudo mount /dev/xxx /media/example
```

To make it permanent
```
gksudo gedit /etc/fstab &
```

In that last one, copy a line of a hard disk that already works, and try to edit the less amount of settings as possible. But... I don't remember how to get the UUID, which is quite important.

---

