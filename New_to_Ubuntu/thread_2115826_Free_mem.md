---
title: "Free mem?"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by CrewDK on 2013-02-14
Please take a look at my screenshot. Why `free` shows that only 1,7 Gb RAM free while `htop` shows, that used only 200-300 Mb from 4Gb RAM?

---

### Post by mcduck on 2013-02-14
Actually "free" says that you have 3753MB of free RAM. ;)

You should be reading from the "-/+ buffers-cache"-line.

The value on the first row includes any buffered data (for example things waiting to be written to your hard drive) and the cache (recently accessed data that is kept in the free part of RAM in case you need it again, avoiding having to read same things from the hard drive again and again. Since cached data can be dropped at any time if some  application needs more memory, it counts as free from the program's perspective)

---

### Post by CharlesA on 2013-02-14
> **mcduck said:**
> Actually "free" says that you have 3753MB of free RAM. ;)

You should be reading from the "-/+ buffers-cache"-line.

The value on the first row includes any buffered data (for example things waiting to be written to your hard drive) and the cache (recently accessed data that is kept in the free part of RAM in case you need it again, avoiding having to read same things from the hard drive again and again. Since cached data can be dropped at any time if some  application needs more memory, it counts as free from the program's perspective)

+1.

This explanation also helps. ;)
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by CrewDK on 2013-02-14
Thanx for explain. :)

---

