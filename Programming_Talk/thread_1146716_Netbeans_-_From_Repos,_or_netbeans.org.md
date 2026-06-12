---
title: "Netbeans - From Repos, or netbeans.org?"
date: 2009-05-02
forum: Programming Talk
---

### Post by novafluxx on 2009-05-02
I began installing Netbeans from the add/remove list, and noticed it was installing OpenJDK/OpenJRE. I already have Sun Java installed, and I was wondering if having both of these will conflict with each other when I attempt to run a Java application? I know as long as the IcedTea isn't installed, I shouldn't have a problem in on websites.

So what do you guys/gals think?

---

### Post by myrtle1908 on 2009-05-04
Firstly, you should get NetBeans from their website as it is the most up-to-date version.

Secondly, Sun's JDK/JRE and the Open* releases can coexist with no problems (at least in my experience).  You can change the default JRE that your system uses by executing the following:-

```
sudo update-alternatives --config java
```

... where you will be prompted to select a JRE as the system default.

---

### Post by sujoy on 2009-05-04
also netbeans bundles the glassfish and tomcat server only with the binaries. the zip files that you can compile yourself, doesnt come with the bundled server.

while you can install tomcat, glassfish seperately, i prefer the bundled server as it gets me running with minimum fuss. :)

---

### Post by MeLight on 2009-05-04
Get it from netbeans.org. I tried both versions, the one you get apt-get install is usually older AND you get a GUI install with the download from the website :D

---

### Post by salvachn on 2009-05-06
The download from the official site has all required plug-ins(choose whatever you need), a GUI installer and has JavaDB, Glassfish, SOA options to boot.

---

