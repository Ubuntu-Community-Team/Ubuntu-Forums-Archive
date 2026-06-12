---
title: "Accessing second harddrive"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by hurdevan on 2008-04-26
I am having trouble accessing my second hardrive becasue the permissions properties have been locked on read only for user and when i try writing to it by starting the Nautilus using 'sudo nautilus' it tells me this hard drive is a read only drive. I can't changes any permissions in root....

Im using Ubunto 7.04

help

---

### Post by scragar on 2008-04-26
try forcing the harddrive to remount, first find the hard-drives refference:
```
mount | grep "\(sdb\|hdb\)"
```
(it will start with /dev/sdb or /dev/hdb )

then force it to remount:
```
sudo mount -o remount,rw **/dev/sdb1**
```
where /dev/sdb1 is your partition.

---

