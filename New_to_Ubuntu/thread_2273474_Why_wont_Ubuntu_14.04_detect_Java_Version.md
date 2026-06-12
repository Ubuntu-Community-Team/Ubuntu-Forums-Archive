---
title: "Why wont Ubuntu 14.04 detect Java Version"
date: 2015-04-13
forum: New to Ubuntu
---

### Post by robertzito on 2015-04-13
So I just installed a network drive that is suppose to allow me remote access through the Western Digital My Cloud. So when I attempt to use the site, it allows me to log in with no problem. When I click on my drive it directs me to [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp) I guess indicating I do not have the proper version of Java installed. So I went through the tutorial and upgraded my Java from 1.7 to the version below, this is the response when I run java -version from the terminal. Is there another version of java that I need for [https://www.wd2go.com/?](https://www.wd2go.com/?)

java version "1.8.0_40"
Java(TM) SE Runtime Environment (build 1.8.0_40-b25)
Java HotSpot(TM) 64-Bit Server VM (build 25.40-b25, mixed mode)

---

### Post by sandyd on 2015-04-13
Don't use that guide, doesn't install java plugin for browser properly sometimes

Try [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

However, we have to remove the java that you installed on your system first. See [https://www.java.com/en/download/help/linux_uninstall.xml](https://www.java.com/en/download/help/linux_uninstall.xml) for instructions on how to do that.

---

