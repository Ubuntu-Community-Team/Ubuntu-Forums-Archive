---
title: "problem in java loading in ubuntu 12.04 lts"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by ravikaushik on 2013-04-22
dear sir
i download the java jdk 6 and 7  and icd tea plugin
to start webex player to watch educational videos
but fire fox cannot connect to the webex player and error occurs'setup error'
how to solve it

---

### Post by Mopar1973Man on 2013-04-22
I'm using actual Java from Oracle software.

This works very well with all web base Java scripts and automatically ties with Firefox.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by siddharth007 on 2013-04-23
On your firefox browser's address bar type this
```
about:plugins
```
This will give you the list of enabled plugins in firefox.If you can see the IcedTea-web plugin,this means that the plugin is integrated with your browser or else you need to integrate the plugin manually.

To do a manual integration with your firefox browser just create a soft link of the **IcedTeaPlugin.so/libjavaplugin.so**file(whichever in applicable in your case) to the firefox plugins directory (/usr/lib/mozilla/plugins) 
```
cd /usr/lib/mozilla/plugins && ln -s $INSTALL/lib/IcedTeaPlugin.so
```
Where $INSTALL is the IcedTea-web installation directory (usually it is /usr/local)

---

### Post by slickymaster on 2013-04-23
> **Mopar1973Man said:**
> I'm using actual Java from Oracle software.

This works very well with all web base Java scripts and automatically ties with Firefox.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

+1
Using this PPA not only you get Oracle Java but also it adds an updater to your software sources and you'll always get the latest java update through ubuntu's software updater.

---

