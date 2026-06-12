---
title: "Compiling netcat-openbsd"
date: 2013-03-09
forum: Packaging and Compiling Programs
---

### Post by besial on 2013-03-09
Any ideas to get this to compile?```
$ sudo apt-get source netcat-openbsd$ cd netcat-openbsd-1.89$ makenetcat.c: In function ‘local_listen’:netcat.c:553:35: error: ‘SO_REUSEPORT’ undeclared (first use in this function)netcat.c:553:35: note: each undeclared identifier is reported only once for each function it appears innetcat.c: In function ‘set_common_sockopts’:netcat.c:775:33: error: ‘SO_JUMBO’ undeclared (first use in this function)make: *** [netcat.o] Error 1
```Thank you

---

### Post by schragge on 2013-03-10
```
sudo apt-get build-dep netcat-openbsd
```

---

### Post by peng6662001 on 2013-03-12
Can anybody fix the error?

---

