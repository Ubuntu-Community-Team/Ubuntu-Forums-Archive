---
title: "Vuze on 12.04"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by tapostol on 2012-11-25
i have just installed ubuntu 12.04 but i can't get vuze running.
I have removed it completely twice and then reinstalled it but it isn't working. I can see the icon, i click on it but nothing happens...:confused::confused::confused:
Any ideas?

---

### Post by zeroseven0183 on 2012-11-25
What happens when you open it through the Terminal?

```
vuze
```

or

```
azureus
```

---

### Post by tapostol on 2012-11-25
unable to start.. Can't figure out why..

[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.16.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/titika/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Shell
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Shell
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 15 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
	at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:679)

---

### Post by tapostol on 2012-11-27
> **zeroseven0183 said:**
> What happens when you open it through the Terminal?

```
vuze
```

or

```
azureus
```


unable to start.. Can't figure out why..
(btw still having the same prob, if you have any suggestions..)

[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.16.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/titika/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ e Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Native MethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(De legatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at org.gudy.azureus2.ui.common.Main.directLaunch(Main .java:229)
at org.gudy.azureus2.ui.common.Main.main(Main.java:13 2)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ e Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Native MethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(De legatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at com.aelitis.azureus.launcher.MainExecutor$1.run(Ma inExecutor.java:37)
at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Shell
at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<i nit>(Initializer.java:111)
at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:8
at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Shell
at java.net.URLClassLoader$1.run(URLClassLoader.java: 217)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.j ava:205)
at java.lang.ClassLoader.loadClass(ClassLoader.java:3 21)
at com.aelitis.azureus.launcher.classloading.PrimaryC lassloader.loadClass(PrimaryClassloader.java:103)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 66)
... 15 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
at com.aelitis.azureus.core.impl.AzureusCoreImpl.crea te(AzureusCoreImpl.java:120)
at com.aelitis.azureus.core.AzureusCoreFactory.create (AzureusCoreFactory.java:46)
at org.gudy.azureus2.ui.common.Main.main(Main.java:16 0)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ e Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Native MethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(De legatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at com.aelitis.azureus.launcher.MainExecutor$1.run(Ma inExecutor.java:37)
at java.lang.Thread.run(Thread.java:679)

---

### Post by zeroseven0183 on 2012-11-30
You need to have Java to run Vuze. Please install Java (JRE) from the Ubuntu Software Center.

---

