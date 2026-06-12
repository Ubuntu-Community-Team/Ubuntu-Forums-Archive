---
title: "Install Java 1.5 not 1.6"
date: 2010-12-30
forum: Packaging and Compiling Programs
---

### Post by Tlingit on 2010-12-30
I'm trying to install Java version 1.5 I don't mind if 1.6 is installed I can figure out how to set alternatives but for some reason I can't find the 1.5 package.

```
apt-cache search java
```
only shows openjava 6

I'm assuming that i don't have the repo with 1.5 does anyone know where I can get it?

---

### Post by SevenMachines on 2010-12-31
I don't know of any repositories to be honest, 1.5 was dropped quite a while ago, after hardy. Downloading and installing the hardy packages might be ok, i'm not sure how much the packaging has changed since then...
[http://packages.ubuntu.com/search?keywords=java5&searchon=names&suite=hardy-updates&section=all](http://packages.ubuntu.com/search?keywords=java5&searchon=names&suite=hardy-updates&section=all)

Or you could maybe try downloading previous versions from oracle if you prefer 
[http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html](http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html)

If you find a repository let me know, for future reference just in case

---

