---
title: "how to install when there is no makefile"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by john77eipe on 2012-04-22
I tried to install utimer ([https://launchpad.net/utimer](https://launchpad.net/utimer)) by following the below steps.
```

$ tar -zvxf utimer-0.4.tar.gz 
$ cd utimer-0.4 /utimer-0.4
$ ./configure /utimer-0.4$ ls  
aclocal.m4  autogen.sh  config.h.in  configure     COPYING  depcomp   INSTALL    
 Makefile.am    Makefile.in  mkinstalldirs  po      README.in AUTHORS     ChangeLog   
config.log   configure.ac  data     Doxyfile  install-sh  Makefile.decl  missing      NEWS           README  src /utimer=0.4

$ make make: *** No targets specified and no makefile found. 


```How shall I proceed?

---

### Post by zombifier25 on 2012-04-22
Try reading the INSTALL file and see what it says.

---

### Post by r-senior on 2012-04-22
Running ./configure should generate the Makefile. It did for me:

```
$ tar -zxf utimer-0.4.tar.gz 
$ cd utimer-0.4
$ ./configure
$ make
```

---

