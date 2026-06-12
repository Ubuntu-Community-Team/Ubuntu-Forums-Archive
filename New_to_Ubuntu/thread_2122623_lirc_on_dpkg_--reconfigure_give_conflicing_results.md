---
title: "lirc on dpkg --reconfigure give conflicing results"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-03-05
mark@Lexington-19:/$ sudo dpkg-reconfigure lirc
ls: cannot access /lib/modules/3.2.0-38-generic-pae/kernel/drivers/staging/lirc: No such file or directory
 * Loading LIRC modules                                                 [ OK ] 
find: `/sys/class/rc/*/': No such file or directory
 * Starting remote control daemon(s) : LIRC                             [ OK ]

What does this mean? Is this a problem? If it is, what should I do?

---

### Post by sully101 on 2013-03-06
If lirc is working then "If it aint broke dont fix it" If you are trying to reconfigure lirc then this thread may help [http://ubuntuforums.org/showthread.php?t=1106463]("http://ubuntuforums.org/showthread.php?t=1106463")

---

