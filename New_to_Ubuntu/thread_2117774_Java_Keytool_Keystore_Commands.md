---
title: "Java Keytool Keystore Commands"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by 007casper on 2013-02-19
Java Keytool Keystore Commands doesnt work with java version "1.7.0"



java -version> 
java version "1.7.0"
Java(TM) SE Runtime Environment (build pxi3270sr3-20121025_01(SR3))
IBM J9 VM (build 2.6, JRE 1.7.0 Linux x86-32 20121024_126071 (JIT enabled, AOT enabled)
J9VM - R26_Java726_SR3_20121024_1635_B126071
JIT  - r11.b02_20120924_26343a
GC   - R26_Java726_SR3_20121024_1635_B126071
J9CL - 20121024_126071)
JCL - 20121019_01 based on Oracle 7u6-b17

> 
keytool -printcert

I get > 
The program 'keytool' can be found in the following packages:
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: apt-get install <selected package>

???

I need to install another jdk for it to read keytool.  I looked at ibm site.  It should work... ???

---

### Post by gordintoronto on 2013-02-19
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.1) (6b27-1.12.1-2ubuntu0.12.04.2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

And keytool is included.

Where did you get the version of Java you have installed?

---

### Post by 007casper on 2013-02-19
I got it from IBM download page
[http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

follow the instructions here
[http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux)

when I look at the IBM documentation, it seems as keytool should work... but it doesnt work

---

