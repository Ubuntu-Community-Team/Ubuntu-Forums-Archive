---
title: "problem with harddisk mountpoint"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by the_bloods_city on 2008-05-11
i have 2 hdd one for windows and linux and the other form my data and when i just try something i put mount point(/) to my data harddisk and after i restart icant access to this harddisk from linux what ihave to do to fix it

ido  when i change mount point 
right click on the drive select properties
 in the drive tab   
in mount point box i put this /
then when i restart my pc i cant access to this drive

---

### Post by annda on 2008-05-11
the / mountpoint is reserved for the root filesystem (meaning your main linux system). for the other disk, you should use something like **/media/**data - you can change "data" to any name you like, but it can't have spaces or special characters, so "data" or "extra_disk" are ok, but "antonio's disk" is wrong.

and where exactly do you put the mountpoint?

---

### Post by clint1010 on 2008-05-30
I had a similar problem

[see this thread for info]("http://ubuntuforums.org/showthread.php?t=792725")

:)

---

