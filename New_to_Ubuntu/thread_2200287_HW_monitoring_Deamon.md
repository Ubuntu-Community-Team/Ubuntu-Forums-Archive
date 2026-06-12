---
title: "H/W monitoring Deamon"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by vishal_agarwal2 on 2014-01-18
Which daemon is responsible for monitoring the H/W related activities. Like if I attach some USB data drive; immediately it reflects at desktop. How does system recognize that some device is added to computer ?

---

### Post by DuckHook on 2014-01-18
"H/W related activities" is too broad. There are many kernel process involved in all of HW. However, if you are asking specifically about USB, then the daemon is *udev*. Wikipedia has a decent [summary]("http://en.wikipedia.org/wiki/Udev") on it.

---

### Post by deadflowr on 2014-01-18
more [udev]("http://manpages.ubuntu.com/manpages/karmic/en/man7/udev.7.html")

---

### Post by vishal_agarwal2 on 2014-01-18
Thanks a lot

---

