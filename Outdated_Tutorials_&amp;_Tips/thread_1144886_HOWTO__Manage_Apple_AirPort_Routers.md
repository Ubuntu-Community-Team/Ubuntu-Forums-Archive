---
title: "HOWTO:  Manage Apple AirPort Routers"
date: 2009-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by spikoley on 2009-05-01
**Overview** 

Apple AirPort routers need special software to manage them.  This HowTo was tested with Jaunty.

You need to download airport-config and sun-java5-jdk.  The airport-config program only works with the older version of Java.  If you run airport-config with the new Java it will do nothing and return you to a command prompt.

**Install airport-utils**

```
sudo apt-get install airport-utils
```

**Install Sun Java 5 JDK**

```
sudo apt-get install sun-java5-jdk
```

**Switch to Sun Java 5 JDK**

```
sudo update-alternatives --config java
```

**Select Sun Java 5 JDK**

```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

In this case it is option 2.

**Run airport-config**

```
airport-config
```

The AirPort Base Station Configurator GUI will open and you can control your AirPort.


**Notes**

When you are finished configuring your AirPort you may need to switch your Java version back for other programs to function properly.

---

### Post by Jesua on 2009-10-27
Thanks.. but do you have any tutorial of how to use the GUI of Airport-utils?

---

### Post by msharelick on 2009-11-01
Hi:

I have an airport base station which I control through my Mac.  I don't want to actually control my base steation, I just want access to the hard drive that is plugged into the usb port.

---

### Post by Firepowerforfreedom on 2009-12-30
The old java5 package is no longer available in the Ubuntu repository! Does anyone know how to get it now?

---

