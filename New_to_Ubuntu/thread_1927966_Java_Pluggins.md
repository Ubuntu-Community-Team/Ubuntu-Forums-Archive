---
title: "Java Pluggins"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Tahinimoon on 2012-02-19
Hi, 
I have Ubuntu 11.10 and use Mozilla Browser.  My Mozilla plug in [Java(TM) Plug-in 1.6.0_30]("http://www.java.com/en/download/manual.jsp") is out of date. In my ubuntu software center this Iced Tea Java 6 Webstart is already installed.

So my questions are: 1. Is the Iced Tea 6 Webstart the same equivalent to the Java TM plug in Mozilla wants updated? 2. If not which is the correct one for Ubuntu and how do I install it? Do I even need it, can I just disable it? 

I'm confused.

---

### Post by gradinaruvasile on 2012-02-19
There are 2 Java implementations on Linux: the open source OpenJDK and the proprietary Oracle Java.
Up until 1.6.26 i think Oracle offered a free license for its proprietary implementation that permits the free distribution in Linux distros. But then they changed their mind and revoked the license so it is not permitted anymore to package Oracle Java in Linux distributions. It can be used for free, but only if you download it directly from their site and configure it manually.
So, that leaves OpenJDK for free distribution since its open source and it contains most code from Oracle Java (actually its the other way around). Now distros package OpenJDK as the default java engine. Its versioning system is different though from that of Oracle Java, it reports version 1.6.24 (i dont know what code is in it, maybe th epatches taht are in .30 java are already in it, but i dont know).
Given that the java detectors on the net are made for Oracle Java, its normal that it reports outdated version.
Icedtea is in fact OpenJDK.

---

### Post by ajgreeny on 2012-02-19
Just for your information, until recently I always installed sun-java packages (now oracle) on my systems rather than the openjdk versions, as there were a few websites that refused to work properly with openjdk, mainly bank webpages.

Recently, either the openjdk packages have improved greatly, or the bank websites have changed, as I now use the openjdk packages with absolutely no problems of any kind.

---

