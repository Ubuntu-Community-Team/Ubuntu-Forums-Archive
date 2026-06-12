---
title: "What's Problem"
date: 2018-02-26
forum: New to Ubuntu
---

### Post by lazyid on 2018-02-26
Excume :)
What's Problem This ?


```
newaliases: fatal: unknown inet_protocols value "ipv4myorigin" in "ipv4myorigin = /etc/mailname"
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kerry_s on 2018-02-26
sudo postfix --configure
or
sudo apt fix install

---

