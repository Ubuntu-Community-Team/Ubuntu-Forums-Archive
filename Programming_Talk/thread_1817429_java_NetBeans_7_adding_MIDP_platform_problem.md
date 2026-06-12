---
title: "java NetBeans 7 adding MIDP platform problem"
date: 2011-08-03
forum: Programming Talk
---

### Post by kaloasd on 2011-08-03
I downloaded the JDK ^ + NetBeans Bundle from here:
[http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html)
and from plugins added the java ME. I tried testing some of the demos but it said I needed a platform so I downloaded J2ME Mobile Information Device Profile (MIDP) 2.0 from here:
[http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javame-419430.html#MIDP-2.0-OTH-G-F](http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javame-419430.html#MIDP-2.0-OTH-G-F) but i cant add it to NetBeans.

---

### Post by kaloasd on 2011-08-04
help

---

### Post by kamaji792 on 2011-11-28
Hi @kaloasd,

I have just started playing around (or more accurately want to start playing around) with Java ME.

I was actually interested in the CDC level devices (i.e. mobile phones).

[LIST]
[*]I installed version 7 of the NetBeans IDE.
[*]I added the **Mobility - Java ME** plugin.
[*]I downloaded the **Sun Java Wireless Toolkit for CLDC 2.5.2** on this page [http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javame-419430.html#sun_java_wireless_toolkit-2.5.2_01b-oth-JPR]("http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javame-419430.html#sun_java_wireless_toolkit-2.5.2_01b-oth-JPR") (file name: [FONT="Courier New"]sun_java_wireless_toolkit-2_5_2-linux.bin[/FONT]).
[*]You have to make the file executable and run it and follow the instructions.
[*]Back to NetBeans **Tools** > **Java Platforms**.  Then click the **Add Platform..** button > Select **Java ME MIDP Platform Emulator** > **Next**.
[*]Browse to the **WTK2.5.2** directory (usually where you downloaded it) > **OK** > **Finish**.
[/LIST]

Now when I create a new project I selected **Java ME** and **Mobile Application**; Set application name and location; Then you get to select the **CLDC** and **MIDP** options.

I came across your post when things were not working for me.  There appear to be later versions of the Platform but not all appear to have Linux versions and some require you to join the Oracle Developer, but I believe the file I point you t0o does not require that.

All the best k

---

