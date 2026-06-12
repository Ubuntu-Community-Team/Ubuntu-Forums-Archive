---
title: "JRE Not Available"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Noble Bell on 2012-08-09
Ok, I have 12.04 installed on my laptop and am slowly learning linux better. I am a developer. I use Java. I cannot, for the life of me, get the JRE to work. 

For instance:

1) I have a jar file that I need to click on and run. Now I have it marked as a executable file. I need to set "Open's with" to be the JRE. I can't. It is not in the list of available programs to open with.

2) When I try and execute "java <program.jar>" from a terminal prompt I get an error:

> 
Exception in thread "main" java.lang.NoClassDefFoundError: textwatermark/jar
Caused by: java.lang.ClassNotFoundException: textwatermark.jar
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
Could not find the main class: textwatermark.jar.  Program will exit.


This jar file works just fine on Windows and Mac.

Thoughts?

TIA

---

### Post by valley1967 on 2012-08-09
Do you have Java installed? if not you may get it from the partner repos

---

### Post by unevenflow on 2012-08-09
**sudo apt-get install openjdk-7-jre icedtea-7-plugin**

or if you prefer Oracle version
[B]sudo apt-get purge openjdk-7-jre icedtea-7-plugin
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-jdk7-installer[/B]
F
For firefox in 32bit Ubuntu:

**sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so 1**

---

### Post by spjackson on 2012-08-09
> **Noble Bell said:**
> 
2) When I try and execute "java <program.jar>" from a terminal prompt I get an error:

That should be
```

java -jar <program.jar>

```shouldn't it?

---

### Post by Noble Bell on 2012-08-09
> **spjackson said:**
> That should be
```

java -jar <program.jar>

```shouldn't it?
Why yes it should. I am embarassed. Thank you guys so much for getting me back on track. I don't recall having to add the -jar switch on Windows but maybe I did and just don't remember it.

---

