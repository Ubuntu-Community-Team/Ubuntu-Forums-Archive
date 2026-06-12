---
title: "azureus won't start"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by bschleusner on 2008-05-06
I am trying to use azureus in Ubuntu 8.04, but I keep getting a weird error.

```
brad@badwulf:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Display
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Display
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 2 more
```

Any idea what exactly is causing this? I am using Ubuntu 8.04 x64 with openJDK.

```
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)

```

---

### Post by Jake90 on 2008-05-07
Well it's possible that it's because you are using the default version of Java and not the sun version. I had that problem with other programs and when I switched to the sun version, everything worked fine.
I'm just curious, what is wrong with transmission? I've tried every bittorrent client I can find, and so far transmission is the fastest. It's also the default client in Hardy.

---

### Post by bschleusner on 2008-05-07
I just switched it to use the sun version of java, but it does the same thing.

I don't use Transmission because it wastes so much bandwidth. It is worthless when there is over 300Mib of fialed download on a 700Mib file.. That is about 4 hours of wasted bandwidth for me.

---

### Post by Jake90 on 2008-05-07
All right, after this I'm out of ideas. Try following this [thread]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/") and let me know if it works. Hopefully it will. Good luck.

---

