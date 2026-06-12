---
title: "[SOLVED] dvdr wont open due to cannot mount error?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-10
i have a dvd-r which i stored a few pdf files on . i did this on windows using the master burn option 


now i want to open up the dvd-r which i copy several ebooks to
but i am getting this error:" Cannot mount volume
Invalid mount option when attempting to mount the volume 'UDF Volume':confused:

---

### Post by aszxcv on 2008-11-10
any help on this error


i want to open up the dvd because the books i have pertained to ubuntu usage

---

### Post by aszxcv on 2008-11-10
any help?

---

### Post by aszxcv on 2008-11-10
:confused::confused:

i really need to get this dvd open it has several linux ebooks that will helped me to stop asking so much questioned here

---

### Post by aszxcv on 2008-11-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a103d34c-1a28-49c0-897a-7caf08135aec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=715ceb56-c466-437b-b309-bc13c3d2daaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by skitter.rusty on 2008-11-11
In the fstab see the line

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Swap udf,iso9660 to iso9660,udf so it looks like this: 

```
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
```

---

### Post by aszxcv on 2008-11-11
i tried to save it with changes but i get "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by skitter.rusty on 2008-11-11
In the terminal type:

```
sudo nano /etc/fstab
```

You shall see the line you have to edit, do so, then pres ctr+x and then press Y.

Try ejecting, if doesn't work, restart and try again.

---

### Post by aszxcv on 2008-11-11
it works thanks a lot  skitter.rusty

i can finally read my  linux ebooks

---

### Post by skitter.rusty on 2008-11-11
> **aszxcv said:**
> it works thanks a lot  skitter.rusty

i can finally read my  linux ebooks
If you could just click the thanks button next to my post (The little medal with a plus sign) Glad I could Help

---

