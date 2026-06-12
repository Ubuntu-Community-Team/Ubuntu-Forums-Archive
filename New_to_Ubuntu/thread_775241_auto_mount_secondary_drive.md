---
title: "auto mount secondary drive"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by DarinB on 2008-04-29
how to set a secondary drive to auto mount in hardy

---

### Post by hopelessone on 2008-04-29
Check the community docs...

Automatic Mount at Boot 
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

HTH...

---

### Post by scragar on 2008-04-29
pick where you want to mount it to, then run```
cat /proc/partition | grep db
```
to see what your partition is called (it's either /dev/sdb1 or /dev/hdb1 ), then:
```
sudo su
mkdir /media/**HD2**
gedit /etc/fstab
```
add the line```
/dev/**sdb1**	/media/**HD2**     auto    defaults        0       2
```
at the end, changning all the bits in bold where nessessary. (where HD2 is the name you want it to appear as, and sdb1 is the partition name).

---

### Post by DarinB on 2008-04-30
didn't work

---

### Post by DarinB on 2008-04-30
ram it as root in a root terminal

---

### Post by DarinB on 2008-04-30
finally git it right thanks

---

