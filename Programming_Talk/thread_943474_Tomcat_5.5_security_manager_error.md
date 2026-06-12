---
title: "Tomcat 5.5 security manager error"
date: 2008-10-10
forum: Programming Talk
---

### Post by djavatar on 2008-10-10
Hello all,

I currently have Tomcat 5.5 running on Ubuntu 8.04 and its working great except for one small hang up.

Every time Tomcat is restarted the first request to a jsp bombs with an exception - java.security.AccessControlException: access denied (java.lang.RuntimePermission accessClassInPackage.org.apache.coyote)

All further requests to jsps work fine. Meaning if I refresh or navigate else where the error is not seen again unless Tomcat is restarted. The error only shows on the very first request to tomcat.  The tomcat logs aren't much help, they show the same exception but they point at the failing jsp: Servlet.service() for servlet org.apache.jsp.index_jsp threw exception.

I have been bashing my head off the wall trying to resolve this. ](*,)  I know its a java security issue but the permissions seem to be correct for org.apache.coyote for jsps. JDK, Tomcat5.5, Tomcat5.5-webapps, and Tomcat5.5-admin were all installed through apt-get.

Any help or insight would appreciated,
Dave

---

### Post by jastazv on 2010-02-24
Hi man. 

I got the same trouble... well... i'll try to find out what it is...

Good luck.

---

### Post by jastazv on 2010-02-24
Well i found a little solution to this problem... this is a very extrange problem... because It only happens on the first request after you restart the server.

Well, just take care that after a restart you have a request... that means that all the other requests will be succesfull... so add this line to the /etc/init.d/tomcat5.5
```

wget http://your.domain.whatever:8180/

```
Just before the else keyword in the start option of the init script... aproximatelly line 174... put it there... 

Every time you restart it... it is going to try to download the index.html ... the "500 Server Internal Error" will continue, but wget knows how to handle this because in spite of this error, it downloads the index.html...

Well, that's all.

Cheers, jastazv.

---

