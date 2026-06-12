---
title: "Jdk 6"
date: 2007-02-03
forum: Programming Talk
---

### Post by ivoencarnacao on 2007-02-03
Heya!

Is there a fast way to install the lastest java's jdk binary from Sun using apt in a clean way, without the need to edit any files?


Thanks!
Ivo.

---

### Post by RedSquirrel on 2007-02-03
All I did was follow the instructions here:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html)

except I think you may need a newer java-package than the one in the repositories.

There's a patched version of that on post #15 of this thread:

[http://www.ubuntuforums.org/showthread.php?t=316980&page=2](http://www.ubuntuforums.org/showthread.php?t=316980&page=2)

---

### Post by phossal on 2007-02-03
Only when someone makes it available. Essentially a third party downloads it from SUN, packages it for Ubuntu, and then "resells" it to you. Someone *has* done that for Java JDK 6, but not until recently. You need to enable the backport repositories, and issue:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by Ramses de Norre on 2007-02-03
It's in edgy backports.

---

