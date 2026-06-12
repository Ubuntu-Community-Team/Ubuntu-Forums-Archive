---
title: "More java compiling problems"
date: 2006-09-27
forum: Programming Talk
---

### Post by L2wis on 2006-09-27
Hey all, i can access java and javac to run and compile programs... but everytime i try to run my compiled program i get this error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: Java/Numeric/bin/
```

Anyone know what i need to do?

Edit*: Some of my older programmed programs run fine and others don't All of which used too :(

Edit**: I've updated the java to be used via:
```
sudo update-alternatives --config java
```

However the following options were only avaalible:
```
  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/j2re1.5-sun/bin/java

```

note. Not : /usr/lib/j2sdk1.5-sun/bin/java

How do i reinstall all this properly?

---

### Post by bukwirm on 2006-09-27
Make sure you are using the Sun compiler and the Sun virtual machine - look in update-alternatives for java and javac.

If you dont have it, the Sun JDK can be installed via the repositories - search in Synaptics for "sun java"

---

### Post by L2wis on 2006-09-27
Thanks, It's all sorted now thanks :) i reinstalled it all with automatix.
Regards

---

