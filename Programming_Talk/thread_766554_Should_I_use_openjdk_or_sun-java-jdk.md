---
title: "Should I use openjdk or sun-java-jdk?"
date: 2008-04-25
forum: Programming Talk
---

### Post by dixon on 2008-04-25
Is openjdk a full impletation of sun-java-jdk? I'm a junior java programmer. Can I run into some issues using openjdk like incompatibility with sun-java-jdk? Mostly I develop desktop applications(used mostly in win) and webpages using mvc frameworks. So the final question is - are there any drawbacks of using openjdk?

---

### Post by jespdj on 2008-04-25
[OpenJDK]("http://openjdk.java.net/") is the open source version of Sun's JDK, but it isn't 100% complete yet.

If you are running 64-bit Ubuntu and you want a Java browser plug-in (to run Java applets in your browser), then use OpenJDK, because the 64-bit version of Sun Java 6 doesn't include a browser plug-in.

Otherwise, if you don't really need applet support, you could use either Sun JDK 6 or OpenJDK. For most things, OpenJDK should work fine at the moment.

Note, you can also install both Sun Java 6 and OpenJDK. With the following command you can choose which Java should be used as the default Java on your system:
```
sudo update-alternatives --config java
```
It will show you a menu in which you can choose which installed Java you want to use by default.

---

### Post by Quikee on 2008-04-25
[This]("http://blogs.sun.com/mr/entry/in_hardy_heron") blog should probably answer you what currently is not supported in OpenJDK that is available in Sun JDK.

---

### Post by piousp on 2008-04-25
For me thre is no reason to use openJDK over the sun-java-jdk. I may be incorrect, but i think that sunjava-jdk is already FOSS.

---

### Post by jespdj on 2008-04-25
> **piousp said:**
> For me thre is no reason to use openJDK over the sun-java-jdk. I may be incorrect, but i think that sunjava-jdk is already FOSS.
It's 96% FOSS and 4% proprietary code - Sun has been working hard the past year on the [OpenJDK project]("http://openjdk.java.net/") to replace the remaining proprietary / non-open code.

---

### Post by piousp on 2008-04-26
> **jespdj said:**
> It's 96% FOSS and 4% proprietary code - Sun has been working hard the past year on the [OpenJDK project]("http://openjdk.java.net/") to replace the remaining proprietary / non-open code.

:KS
Thanks for the info!! 96% FOSS! Thats really incredible!

---

### Post by dixon on 2008-04-27
Thank you for your answers - I'll stick with sun-java-jdk for now....

---

