---
title: "[SOLVED] acer 5051 slow boot"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by thehellboy on 2008-08-18
hi all,
i'm using ubuntu7.04 gutsy.. mine is acer aspire 5051,1 gb ram ,amd ati 1100 radeon xpress. boot up takes nearly 4 min. i dont know why..please some one help solvin this problem

---

### Post by oliviacond on 2008-08-18
try this:
[http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html](http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by nicedude on 2008-08-18
try installing a utility called bootchart it will create nice picture of what takes how long during bootup. It places the picture graph in a directory each time you boot so you can check what is the culprit.

COMMAND TO INSTALL IT
sudo apt-get install bootchart

I don't think you even have to run it after install I think it works automatically ( been awile since I messed with it )

Once you install it and reboot open this folder to see the charts it creates

/var/log/bootchart

Hope this helps you see what is wrong, post the result here and maybe we can all help.

---

### Post by thehellboy on 2008-08-18
thanks dudes.. boot time reduced from 3.5 min to 19 sec,.. amazing isn't it..

---

