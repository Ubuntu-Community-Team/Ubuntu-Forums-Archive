---
title: "ubuntu disc space"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2012-12-07
Im getting a full indication on my shared ubuntu setup.  After I did a search I found df -h and it identifies /dev/sda1 having 5.5gb used and I cant figure out why it is using so much.  I did empty the trash as it mentioned per the warning.  Also my shared says I am using 76gb.  Ideas for cleaning house?

---

### Post by snowpine on 2012-12-07
Can you post the output of df -h as that will help us help you?

5.5 is much too small for a / (root) partition in my opinion.

---

### Post by graphicsmanx1 on 2012-12-07
/dev/sda1 5.5
udev 4.0K
tmpfs 1016K
none 0
none 152K
shared 76G

---

### Post by snowpine on 2012-12-07
Is that really the full & complete copy & pasted output of 'df -h'? Anyway, I recommend to boot with a Linux Live CD/USB and resize your /dev/sda1 as 5.5gb is much too small for Ubuntu in my experience/opinion. I personally use Debian (similar to Ubuntu but not exactly the same) and I have 10gb / partition with separate /boot and /home.

---

### Post by ibjsb4 on 2012-12-07
Bleachbit, its in the software center.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by dannyboy79 on 2012-12-07
> **snowpine said:**
> Is that really the full & complete copy & pasted output of 'df -h'? Anyway, I recommend to boot with a Linux Live CD/USB and resize your /dev/sda1 as 5.5gb is much too small for Ubuntu in my experience/opinion. I personally use Debian (similar to Ubuntu but not exactly the same) and I have 10gb / partition with separate /boot and /home.
that's only displaying how much space is used, not what the entire partition has available. we don't know how large is / partition is.

OP, have you checked /var/log/ for any large log files? Sometimes repeating messages in either kern.log or syslog take up a lot of space in log files.

you can run sudo apt-get clean and sudo apt-get autoclean that may free up some space.

---

