---
title: "Where is catalina.properties ???"
date: 2006-09-19
forum: Programming Talk
---

### Post by alis on 2006-09-19
I have installed tomcat5 using Synaptic Packege Manager but I can find catalina.properties in conf nor using locate.

Please some one help me to find it or to find out y I can't find it.

---

### Post by firebadger on 2006-09-20
I don't tend to install tomcat using the debs, but I would guess that if it isn't in $CaTALINA_HOME/conf then it will probably be in /etc/tomcat

---

### Post by alis on 2006-09-20
No it wasn't there?!?!

---

### Post by Gustavo Orair on 2006-09-26
If you are searching for catalina.policy, you can edit the catalina.policy editing eache one of the /etc/default/tomcat5/policy.d/*.policy files

---

### Post by alis on 2006-09-30
I have founded theme (/etc/default/tomcat5/policy.d/*.policy) but I exactlly mean "catalina.properties".](*,)

---

### Post by XKSIS on 2007-03-01
i've got the same problem 
i ve  created catalina,proteprties file in /var/lib/tomcat5/conf/ folder and tomcat doesn't start showing this in log -->

java.lang.NullPointerException
        at org.apache.catalina.security.SecurityClassLoad.loadCorePackage(SecurityClassLoad.java:53)
        at org.apache.catalina.security.SecurityClassLoad.securityClassLoad(SecurityClassLoad.java:39)
        at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:200)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:402)

if i delete the file again , tomcat is running 

please help :D

---

