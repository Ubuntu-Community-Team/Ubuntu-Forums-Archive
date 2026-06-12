---
title: "Installing Netbeans.  Where is the JDK?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-03
Hi Folks,

I'm installing netbeans.  I've gone to java.com, downloaded the jdk converted it with alien and installed it with dpkg.

But the Netbeans installer still cannot find the JDK.

Does anyone know what it is looking for?

Thanks!

Ray

---

### Post by RealPSL on 2008-10-04
You could have install the JDK directly from Synaptic or apt-get. The package names are sun-java5-jdk for Java 5 and sun-java6-jdk for Java 6. Maybe the Netbeans installer is expecting JAVA_HOME to be set? Does the command ```
which java
``` return the location? If not I would use ```
sudo apt-get install sun-java6-jdk
``` which will ensure that it is seen.

---

