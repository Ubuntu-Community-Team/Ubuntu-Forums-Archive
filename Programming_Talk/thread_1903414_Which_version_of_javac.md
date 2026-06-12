---
title: "Which version of javac ?"
date: 2012-01-02
forum: Programming Talk
---

### Post by donsy on 2012-01-02
My version of java is:

```
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

```If I install openjdk-7-jdk would it be compatible with my java version or should I install openjdk-6-jdk ?

---

### Post by PaulM1985 on 2012-01-02
I am fairly sure that older versions of Jre are not compatible with newer versions of jdk, so I would recommend 1.6. 

Paul

---

### Post by dwhitney67 on 2012-01-02
Doesn't the JDK include the JRE?

I'm not familiar with OpenJDK, but with Sun (now Oracle) JDK, it does.

---

### Post by PaulM1985 on 2012-01-02
> **dwhitney67 said:**
> Doesn't the JDK include the JRE?

I'm not familiar with OpenJDK, but with Sun (now Oracle) JDK, it does.

That was one thing I wasn't sure on which is why I suggested v6 to play it safe.

---

### Post by KdotJ on 2012-01-02
Bare in mind of course that you'll need the JRE-7 if you want to run programs that use JDK-7 specifics. I thought the JDK comes with the JRE as dwhitney67 suggested, but I can't confirm.

---

### Post by maxino on 2012-01-03
If you install openjdk-7-jdk, you should have both JRE and JDK 1.7 on your system.
But do not forget to "tell" your system to use JRE 1.7 afterwards, using ```
update-alternatives --config java
```

Hope this helps

---

### Post by HotCupOfJava on 2012-01-03
It may not be absolutely necessary, but you can uninstall the Java6 JRE and then install the Java7 JDK (which will also give you the Java7 JRE) to be safe.

---

