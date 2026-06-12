---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-08-23
forum: New to Ubuntu
---

### Post by masood4 on 2015-08-23
I tried to install java 1.8 in my ubuntu 14.04. but this error is big barrier!! please help me!
```
download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by aeden.d on 2015-08-28
[SIZE=2]Have you tried installing OpenJDK Java 7 from the repos?

If you want Oracle Java 8 you will need to install from a ppa (ppa:webupd8team/java) but keep in mind the ppa is not officially supported [/SIZE]

---

### Post by QIII on 2015-08-28
Hello!

Would you please let us know what commands you issued leading up to that warning?

---

### Post by Yellow Pasque on 2015-08-28
> download failed

Are you using a proxy or behind a firewall?

---

