---
title: "How do I install .jar files etc"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by lolful64 on 2013-03-18
I never thought I would be back but I am. *thoughts*nobody cares me-:(

Anyways, like the question says how do I install .jar files CORRECTLY. I have minecraft for linux and I don't want to mess up the installation

---

### Post by Cheesemill on 2013-03-18
You don't install .jar files, you just run them from wherever you have downloaded them to using the java command.

---

### Post by QIII on 2013-03-18
... which is

```
java -jar /path/to/file.jar
```

This assumes that you have Java installed.  If you don't, you have to install Java.

---

### Post by slickymaster on 2013-03-18
You can check if you have it just by running the Java version command from terminal.
```
java -version
```

---

### Post by lolful64 on 2013-03-19
> **slickymaster said:**
> You can check if you have it just by running the Java version command from terminal.
```
java -version
```
I have no java what so ever

---

### Post by Cheesemill on 2013-03-19
To install Java just open a terminal and run the following 3 commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Source...
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

