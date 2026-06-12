---
title: "Is the Java 6 shipped with Ubuntu 7.04"
date: 2007-09-06
forum: Programming Talk
---

### Post by shoaibnawaz on 2007-09-06
Java is shipped with Ubuntu 7.04.
What does it mean?

Is it only runtime or SDK as well?

If it is SDK too then how to configure it with Eclipse IDE.

---

### Post by Sensenseppl on 2007-09-06
I don't think that it is shipped with the SDK, but it is easily installed and configured within 5 minutes.

Do you want to develop java using the live-cd?

---

### Post by shoaibnawaz on 2007-09-06
Please visit [Here]("http://devnulled.com/content/2007/04/java-6-shipped-with-ubuntu-704/")

---

### Post by Quikee on 2007-09-06
Java 6 SDK should be in the repositories (multiverse or restricted IIRC)

To set Java 6 to be used by Eclipse (downloaded, not the one from repository) this 2 things should also be done:
[LIST]
[*]**sudo update-java-alternatives -s java-6-sun** -> to set suns java 6 as default jvm used in the system
[*]**sudo gedit /etc/jvm** -> edit jvm configuration and put path to java-6-sun on top of the list.
[/LIST]

---

### Post by fct on 2007-09-06
These are the Sun Java packages included in Ubuntu Feisty 32-bit for the multiverse repositories:

```
$ apt-cache search sun-java
sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture dependent files)
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)
sun-java5-plugin - The Java(TM) Plug-in, Java SE 5.0
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files

```

Apart from that you can install IDEs like netbeans (I suggest that for fast GUI development) and Eclipse (that is really nice save for the lack of an intuitive GUI editor).

As said before, you need to use update-alternatives to make sure the system is set up to use Sun's java and not the gcj compiler, which isn't as good.

---

