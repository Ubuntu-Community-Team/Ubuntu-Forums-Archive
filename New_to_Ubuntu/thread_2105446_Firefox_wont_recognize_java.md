---
title: "Firefox wont recognize java"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by TheTardis on 2013-01-16
I can't find anything on google detailing my specific error.

I located the libnpjp2.so file in my java package, and I have used the ln -s command to make a link to its location in my /usr/lib/mozilla/plugins folder. I check the plugins folder and libnpjp2.so is there, but when I open firefox and check the plugins it is still not listed, as well as any java-based applications will not run.

Im using firefox 18 with Java 7 update 11 (I think so at least, the file is** jre1.7.0_11**) on Ubuntu 12.04

---

### Post by iMac71 on 2013-01-16
[FONT=Verdana]run the following command in a Terminal window:[/FONT]```
[SIZE=2][COLOR=#000000][FONT=Verdana]sudo apt-get install -y openjdk-7-jre icedtea-7-plugin[/FONT][/COLOR][/SIZE]
```

---

### Post by TheTardis on 2013-01-16
That worked great, thanks :D

---

