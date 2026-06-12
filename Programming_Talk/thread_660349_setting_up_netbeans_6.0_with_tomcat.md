---
title: "setting up netbeans 6.0 with tomcat"
date: 2008-01-06
forum: Programming Talk
---

### Post by jcankrom on 2008-01-06
I'm running Debian Lenny, up to date.
I've installed netbeans 6.0 and tomcat 5.5 (-admin, -webapps) through the debian repos.
in netbeans i try to start a new web application project. it asks me to register a server, which i try to set up as a tomcat 5.5 server. it then asks for the catalina home folder. where is that exactly? i'm looking in /etc/tomcat5.5, but see no folder named catalina

what am i missing? is there a catalina package?
this filelist says catalina comes in tomcat5.5-admin package:
[http://packages.debian.org/lenny/tomcat5.5-admin/all/filelist](http://packages.debian.org/lenny/tomcat5.5-admin/all/filelist)

thx

---

### Post by AlexThomson_NZ on 2008-01-06
$CATALINA_HOME (if I'm not mistaken- it's been a while) should just be the install directory of tomcat.

---

### Post by crossdelena on 2008-03-11
The precise directory would be....```
 /usr/share/tomcat-5.5
```

-Cross

---

