---
title: "Slow start up process"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-11
Hello, 

I notice that during Boot, my system will halt for a while at " Waiting for root file system". Is there any tweak to expedite this process so that Ubuntu (mine) will be boot faster than XP (i'm dual booting)

---

### Post by compiledkernel on 2008-06-11
Its possible. You can turn services off that might be slowing up your system. First Id check System > Administration > Services. You can remove some items there ( be careful, for example dont really want to stop anything syslog or cron related). 

There is also a command line tool called sysv-rc-conf. This application will change the run levels of certain services on your system. I caution the use of it, if not careful it can make your system non bootable. 

This guide explains it -- [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by philinux on 2008-06-11
> **wariskampar said:**
> Hello, 

I notice that during Boot, my system will halt for a while at " Waiting for root file system". Is there any tweak to expedite this process so that Ubuntu (mine) will be boot faster than XP (i'm dual booting)

Could you provide your system specs and which version of ubuntu you're running.

---

### Post by wariskampar on 2008-06-11
I'm using Hardy Heron, Intel Pentium M 1.83Ghz, 1Gb RAM, HP Pavilion dv4000.

---

### Post by MyR on 2008-07-04
workaround here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003)

peace

---

