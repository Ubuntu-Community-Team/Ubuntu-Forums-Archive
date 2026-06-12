---
title: "[SOLVED] How can i use eclipse in Ubuntu"
date: 2007-09-02
forum: Programming Talk
---

### Post by chongchongworks on 2007-09-02
Hi, I just started to use Ubuntu a few days ago. I installed Eclipse, then I realized I did not install jdk yet, so I add Jdk1.5, but Eclipse looks cannot find it, because the "classpath" in building option says JRE_LIB:****jre1.4****, and it does not allow me to change it. And I cannot run java program, which I can run in windows.

I try to make some mistake, like "public static" to " public statc", it does not give any warning, so I guess it did not import the library of jdk. I uninstall eclipse and reinstall it, the problem still there. So how can i fix it?

Thanks.

---

### Post by Compyx on 2007-09-02
This thread: [http://ubuntuforums.org/showthread.php?t=368058&highlight=eclipse+java+runtime]("http://ubuntuforums.org/showthread.php?t=368058&highlight=eclipse+java+runtime")
should be of some help, of course replacing the version number of the JDK/JRE with the one you've installed.

---

### Post by xlinuks on 2007-09-02
If you still experience problems you might consider installing NetBeans which comes bundled with the latest version of JDK so you don't have to configure path variables and so on ( Eclipse and NetBeans are both high quality free software).
[http://java.sun.com/javase/downloads/netbeans.html](http://java.sun.com/javase/downloads/netbeans.html)

---

### Post by CptPicard on 2007-09-02
If you added jdk1.5 from the repositories, try 

```

yourbox$ sudo update-alternatives --config java

```

It gives you a list of alternatives, choose the Sun 1.5 one.

---

### Post by realstraw on 2007-09-02
Click widow->preference you can add the library by select where you installed your java directory. e.g. /usr/lib/jvm/java-6-sun

---

### Post by chongchongworks on 2007-09-04
This worked:

Window/Preferences/Java/Installed JRE's, then add the /usr/lib/jvm/java-1.5.0......

Thank all above guys

---

