---
title: "Java Permission Error?"
date: 2009-08-29
forum: Programming Talk
---

### Post by dragos240 on 2009-08-29
Hi, I have created a jnlp xml script that will open a web applet. I do NOT have the source.

The XML is as follows:
```

<?xml version="1.0" encoding="utf-8"?>
<jnlp
  spec="1.0+"
  codebase="file:///home/harley/Meltdown/meltdown"
  href="meltdown.jnlp">
  <information>
    <title>Meltdown</title>
    <vendor>JaGeX Ltd.</vendor>
    <description>:)</description>
    <offline-allowed/> 
    <shortcut online="true"> 
      <desktop/> 
      <menu submenu="meltdown"/> 
    </shortcut>
  </information>
  <resources> 
    <j2se version="1.6+" initial-heap-size="32m" max-heap-size="512m"/>
    <jar href="meltdown2.jar" download="eager" main="true"/>
  </resources>
  <application-desc main-class="meltdown"/>
</jnlp>

```

It can open the main "meltdown.class" file. But not one (or possibly all) of the graphics.

Here is the error:
```

java.security.AccessControlException: access denied (java.io.FilePermission jagex/logo.gif read)
    at java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)
    at java.security.AccessController.checkPermission(AccessController.java:546)
    at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
    at java.lang.SecurityManager.checkRead(SecurityManager.java:871)
    at sun.awt.SunToolkit.getImageFromHash(SunToolkit.java:871)
    at sun.awt.SunToolkit.getImage(SunToolkit.java:885)
    at b.a(Unknown Source)
    at b.a(Unknown Source)
    at a.a(Unknown Source)
    at meltdown.main(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.sun.javaws.Launcher.executeApplication(Launcher.java:1468)
    at com.sun.javaws.Launcher.executeMainClass(Launcher.java:1414)
    at com.sun.javaws.Launcher.doLaunchApp(Launcher.java:1225)
    at com.sun.javaws.Launcher.run(Launcher.java:114)
    at java.lang.Thread.run(Thread.java:619)

```

What is wrong?

---

