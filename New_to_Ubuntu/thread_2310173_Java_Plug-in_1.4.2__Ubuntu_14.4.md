---
title: "Java Plug-in 1.4.2  Ubuntu 14.4"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by salvatore7 on 2016-01-16
Hi folk! 


I am new to Ubuntu, I am using 14.04 LTS. I need the plugin [_Java Plug-in 1.4.2         _       ]("http://java.sun.com/javase/downloads/index.jsp")in order to download some data that I need, but I tried from the website suggested or using apt-get install. However I did not succeed. Could you please help me?

---

### Post by bashiergui on 2016-01-16
You can install it by typing ```
sudo apt-get install openjdk
``` Or you can search for java in the software center.

---

### Post by sandyd on 2016-01-16
If you need Oracle Java in particular, see [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html) instead

---

### Post by salvatore7 on 2016-01-17
When I try to install it using the terminal I get this:

E: Unable to locate package openjdk

---

### Post by Vasilis_Papapanagi on 2016-01-17
Perhaps you need to try
```
sudo apt-get update
```
first.

---

### Post by matt_symes on 2016-01-17
Hi

As sandyd suggested, if you need Oracle Java specifically then install from the PPA.

However if Oracle is not specifically required then you can install Java from the repositories.

You need to specify the version of Java you want to install though.

The available versions in the 16.04 repositories are:

```
matthew-xu-16-04:/home/matthew:0 % acse ^openjdk-\[0-9\]-jre$
openjdk-7-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-8-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-9-jre - OpenJDK Java runtime, using Hotspot JIT
matthew-xu-16-04:/home/matthew:0 % 
```

So to install version 8 you would use

```
sudo apt-get install openjdk-8-jre
```

To check what versions you have on your system (as they may be different from mine), run this command in the terminal.

```
apt-cache search ^openjdk-\[0-9\]-jre$
```

Pick the version you need and install it.

Kind regards

---

