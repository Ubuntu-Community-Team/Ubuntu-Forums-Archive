---
title: "Need to install java 5 and  tomcat server in ubuntu"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by teenzonez on 2008-08-16
Hi could anyone help me to install java 5 and tomcat server on ubuntu? do i just need to select all the java relatd package from synaptic package manager?
Thanks,
Teena

---

### Post by CloudFX on 2008-08-16
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

Will install the latest java.  However, I'm not entirely sure about java 5.  Is this version necessary?  I believe only tomcat 5.5 is available in Hardy.

---

### Post by datajelly on 2008-08-26
I recently had to re-install Tomcat 6 and [I wrote down my steps]("http://blog.datajelly.com/2008/08/installing-apache-tomcat-6-on-ubuntu.html") (mainly for my own future reference). I don't know if you'd be open to switching to Tomcat 6?

From what I've seen, Tomcat 5.5 is the most recent version available from apt-get, so I guess you could always go that route as well...

---

