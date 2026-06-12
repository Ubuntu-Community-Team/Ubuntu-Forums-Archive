---
title: "Jdownloader doesn't start"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by Tassadar on 2013-07-10
Hi all,

I'm using kubuntu 13.04 x64 and I'm trying to install jdownloader.

My stepts have been:

Install Java
```
sudo apt-get install openjdk-7-jdk openjdk-7-jre
```

Download and install jdownloader:
```
wget http://installer.jdownloader.org/jd_unix_0_9.sh
sudo chmod +x jd_unix_0_9.sh
sudo bash ./jd_unix_0_9.sh
```

Then jdownloader starts ok and works, update himself and all this stuff.

The problem comes when I restart, then if i try to run jdownloader it seems to be loading for a moment but nothing, and if i try to run the updater I get this error:

 
```
java.lang.NoClassDefFoundError: jd/gui/UserIO

    at jd.utils.JDUtilities.getDatabaseConnector(JDUtilities.java:876)
    at jd.config.SubConfiguration.<init>(SubConfiguration.java:77)
    at jd.config.SubConfiguration.getConfig(SubConfiguration.java:106)
    at jd.update.WebUpdater.getConfig(WebUpdater.java:74)
    at jd.update.Main.main(Main.java:121)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
    at com.install4j.runtime.launcher.Launcher.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: jd.gui.UserIO
    at java.net.URLClassLoader$1.run(URLClassLoader.java:366)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:423)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:356)
    ... 11 more
```

¿Any help?

Many thanks in advance

---

