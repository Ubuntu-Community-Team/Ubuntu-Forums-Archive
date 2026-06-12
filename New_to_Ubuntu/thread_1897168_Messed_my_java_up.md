---
title: "Messed my java up"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by getut on 2011-12-18
I have had java working at points on my 11.10 64 bit machine but java is screwed up now.

I am TRYING to get everything working on OpenJDK 7 only but am failing miserably. No matter what I do it pulls in openjdk 6.

Currently if I run java -version from terminal it says:
java version "1.7.0_147-icedtea"
OpenJDK Runtime Environment (IcedTea7 2.0) (7~b147-2.0-0ubuntu0.11.10.1)
OpenJDK 64-Bit Server VM (build 21.0-b17, mixed mode)

Which is what I want, but if I try to run a java app such as minecraft and right click on a jar file, it only offers openjdk 6 to me to run it with. Minecraft will run and let me sign in but goes to a black screen and stays there after signing in.

Testing java through the web browser shows:
Vendor: Sun Microsystems Inc.
Version: Java SE 6 Update 23

Please help.

---

### Post by BC59 on 2011-12-18
You could try to install Oracle Java 7.
[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

If you see to link, after installing it, you have to delete the old plugin from Firefox.
Look if you can do something like this for Minecraft.
A solution could be:
```
sudo apt-get purge sun-java6-jdk sun-java6-jre sun-java6-bin sun-java6-plugin
``` but I didn't try it.

---

