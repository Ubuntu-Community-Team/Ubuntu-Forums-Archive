---
title: "Netbeans 5.5 bundle"
date: 2006-11-08
forum: Programming Talk
---

### Post by tylerjames on 2006-11-08
Hey guys,

Unfortunately, for a school group project, I've been forced to use Netbeans 5.5 (it's hell). And worse, I haven't been able to install it for ubuntu yet so I've been forced to use windows (double hell).

We have to use Netbeans 5.5 with the Sun Java Application Server (apparently Tomcat doesn't support some of the features we need).

There is a bundle on the Netbeans site that includes some J2EE tools. That is what we were instructed to install. Unfortunately they only have packages for Windows, Solaris, and RedHat...

Has anyone successfully been able to install Netbeans 5.5 with the Sun server? If so could you please let me know how? I really want to divorce myself from the whole windows mess.

Thanks!

---

### Post by nsleiman on 2006-12-15
well i have Netbeans5.5 installed on my ubuntu box and it has never rendered an error :)

as for tomcat its bundled in so no need to install,

befor installing netbeans make sure you have the JVM installed, sun5 is fine.

maybe you have to set the JAVA_HOME=\usr\lib\... in the /etc/environment
.

good luck

---

