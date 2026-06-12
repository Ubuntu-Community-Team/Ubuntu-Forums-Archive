---
title: "The Mystery of Missing Java"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by kaspar_silas on 2008-07-09
Hi All,

I have installed java and even if I retry with:
sudo apt-get install javajdk-6-jre-headless
I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre-headless is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

However typing java -version gives:

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>

Any one know what the break out of this infinite loop is. Any help greatly appreciated.

---

### Post by S1xp4ck on 2008-07-09
Hi, perhaps try the following to get java up and running.  This will install the Sun-Java Runtime.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
  
Once installed then type

```
java -version
```

To verify version again.  You should get something like:

java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)
Java HotSpot(TM) Server VM (build 1.5.0_15-b04, mixed mode)

(keep in mind I have java 1.5.0 installed yours will be a 1.6 vesrion)


You can also select what java is default if you have alternatives installed as well by typing

```
sudo update-alternatives --config java 
```


Hope this helps.

---

### Post by kaspar_silas on 2008-07-09
Thanks,

I had the runtime installed but the java was defaulted to something wrong. So the second command sorted it.

Much Obliged

---

