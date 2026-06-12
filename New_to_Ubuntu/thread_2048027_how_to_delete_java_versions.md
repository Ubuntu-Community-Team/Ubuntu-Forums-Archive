---
title: "how to delete java versions"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by 007casper on 2012-08-26
I have too many different versions of java.

> java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
Try: apt-get install <selected package>


what is the proper way of removing these packages?

---

### Post by Paqman on 2012-08-26
Just uninstall them. Either open up Ubuntu Software Centre (or Synaptic if you have it) or use:
```
sudo apt-get remove packagename
```

---

### Post by 007casper on 2012-08-26
thank you

---

### Post by davesmith on 2012-08-26
Alternatively, you could use a script from Duinsoft. This removes all old versions of java, downloads the current version for Ubuntu and installs the current sun-java:-  [http://www.duinsoft.nl/packages.php](http://www.duinsoft.nl/packages.php)  the current Oracle version is Java 7 update 5. The link has a good howto

---

