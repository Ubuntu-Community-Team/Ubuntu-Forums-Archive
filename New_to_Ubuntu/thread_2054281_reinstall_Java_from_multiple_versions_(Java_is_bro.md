---
title: "reinstall Java from multiple versions (Java is broke)"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-09-07
I have a .jar file on my desktop and when I right click it, I get "Open with Archive Manager" by default (I have made it executable by right-clicking and going to Properties)

also when right-clicking, I get an "Open with" menu with two options "OpenJDK Java 6 Runtime" and "Sun Java 6 Runtime"

...java is just giving me problems - so I want to uninstall all these versions and reinstall just one

```
user@Computer:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```

---

### Post by androssofer on 2012-09-07
> **TooFreppaT said:**
> I have a .jar file on my desktop and when I right click it, I get "Open with Archive Manager" by default (I have made it executable by right-clicking and going to Properties)

also when right-clicking, I get an "Open with" menu with two options "OpenJDK Java 6 Runtime" and "Sun Java 6 Runtime"

...java is just giving me problems - so I want to uninstall all these versions and reinstall just one

```
user@Computer:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```

try:

```
sudo apt-get --purge remove openjdk-6-jre
```

then:

open the software centre and install Java from it.. 

for Minecraft I use J|ava 6, but you might prefer java 7..

---

### Post by TooFreppaT on 2012-09-08
thanks :)

---

