---
title: "problems installing java	](*,)"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by jaktheripper on 2008-06-25
user@Datalyst:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

...what should I do to correct this? Im totally new to any OS other than Windows...

---

### Post by cozmicharlie on 2008-06-25
You have the wrong java version.  Did you install the Ubuntu Restricted Extras?  Copy or cut and paste the following.

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

That should work for you.

---

### Post by stchman on 2008-06-25
> **jaktheripper said:**
> user@Datalyst:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

...what should I do to correct this? Im totally new to any OS other than Windows...

If you are using 32 bit do the following:
```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

64 bit do the following:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

This will do you.  The gcj browser plugin is pretty good, but not as good as the SUN one.

---

### Post by JudgeFudge on 2008-06-25
I think you forgot a hyphen, i.e:

java -version

is the command to show what java version you are running.

---

### Post by avtolle on 2008-06-25
If the OP is running a 64-bit system, the sun plugin isn't going to work. There's supposed to be a 64 bit plug in soon, but if running a 64 bit system, I think that the open java is what is available right now (without some work).

---

### Post by stchman on 2008-06-25
> **avtolle said:**
> If the OP is running a 64-bit system, the sun plugin isn't going to work. There's supposed to be a 64 bit plug in soon, but if running a 64 bit system, I think that the open java is what is available right now (without some work).

All the SUN Java packages are 64 bit BESIDES the browser plugin.

---

### Post by avtolle on 2008-06-25
I understand that everything but the plugin is or can be 64 bit; but, and I could well have misunderstood the OP initially, I thought there was a problem in the browser.

---

### Post by jaktheripper on 2008-06-25
righteous, im totally new to any linux type OS so im learning from step one. thanks for the help i appreciate it

---

### Post by cozmicharlie on 2008-06-26
Glad it helped.  If this worked, please post what you did and mark this thread "solved" so others can benefit.

Thanks

---

