---
title: "installin in Java Swing in UBUNTU"
date: 2009-04-20
forum: Programming Talk
---

### Post by ggankhuy on 2009-04-20
Can someone tell me how to install the Java Swing package so that
something like below will build?

import java.swing.*;


thanks!

---

### Post by Usse on 2009-04-21
the swing package is in the jdk environment.. you just need to install the jdk.

---

### Post by jespdj on 2009-04-21
Note that it is java**x**.swing, not java.swing.

Swing is a standard part of Java, you don't need to install anything special besides the JDK.
```
sudo apt-get install sun-java6-jdk
```

---

