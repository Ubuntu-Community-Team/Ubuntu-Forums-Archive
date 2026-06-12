---
title: "Request help installing Java EE 6 tutorial required software"
date: 2011-11-19
forum: Repositories &amp; Backports
---

### Post by thundercleese on 2011-11-19
I am trying to install the required software for the Java 6 EE tutorial, but am having no luck.  Can someone please assist me with the commands to install? 

I am running Ubuntu 11.10.

Tutorial Software list: [http://download.oracle.com/javaee/6/tutorial/doc/gexaj.html](http://download.oracle.com/javaee/6/tutorial/doc/gexaj.html)

Thank you.

EDIT:
I should add I tried:

sudo apt-get update

sudo apt-get install sun-java6-jdk  sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate
E: Package 'sun-java6-jre' has no installation candidate

---

### Post by jorok_tupur on 2011-11-19
Hi,

Since Ubuntu 11.10, Sun's JDK is no longer included in the repository. Try OpenJDK.
```
sudo apt-get install openjdk-6-jdk
```

---

