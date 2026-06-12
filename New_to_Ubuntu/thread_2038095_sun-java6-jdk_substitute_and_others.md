---
title: "sun-java6-jdk substitute and others"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by 007casper on 2012-08-05
I know the substitute for sun-java6-jdk is openjdk-6-jdk

what are the substitute for the ones down below?
sun-java6-jre
sun-java6-plugin 
sun-java6-fonts 4

??

---

### Post by QIII on 2012-08-05
Don't use 6 at all.  Both OpenJDK 6 and Oracle Java 6 are vulnerable to security exploits and reach EOL in November.

Install OpenJDK 7 or Oracle Java 7 Update 5.

OpenJDK 7 can be installed from the repos.

For Oracle Java 7 Update 5, see the link titled "Using webupd8.org's strikingly simple method" in the Oracle Java 7 section in the Java wiki in my signature.

Either of those methods will install the JRE, the JDK and the browser plugin.

Be aware that OpenJDK 7 is not universally recognized, even though it is the open source reference implementation of Oracle Java 7.

---

