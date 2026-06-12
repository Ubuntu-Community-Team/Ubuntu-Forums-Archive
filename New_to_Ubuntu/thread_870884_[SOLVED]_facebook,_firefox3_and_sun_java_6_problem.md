---
title: "[SOLVED] facebook, firefox3 and sun java 6 problem"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by wolfie2x on 2008-07-26
facebook photo uploader applet on firefox.3.0.1 with sun-java6-plugin was always crashing on me. (Ubuntu 8.04; sun-java6-jre and sun-java6-plugin)
after hours of googling and hair-pulling, here's the workaround that worked for me; hope it helps someone..

* install sun-java5-jre and sun-java5-plugin from synaptic pkg mangr.
* use the following to set the jre and plugin to java5

$ sudo update-alternatives --config java     // select java5 here.
$ sudo update-alternatives --config xulrunner-1.9-javaplugin.so  // select java5 plugin 

* restart firfox and verify the plugin version by going to tools>add-ons and plugins tab and check for Java(TM) plugin 1.5.0 ...

hopefully that should work. :guitar:

---

### Post by LinuxRocks713 on 2008-07-28
> **wolfie2x said:**
> facebook photo uploader applet on firefox.3.0.1 with sun-java6-plugin

<snip size="huge"></snip>


A photo upload should **NOT** require a JRE; HTTP POST should have worked just fine.

---

### Post by stevoo on 2008-07-28
POST ... depending from how they develop it. 
But they are using mostly flash stuff and as flush is a bit buggy .... well it is causing the crash !

---

### Post by wolfie2x on 2008-07-29
> **LinuxRocks713 said:**
> A photo upload should **NOT** require a JRE; HTTP POST should have worked just fine.

can HTTP POST do a quick selective upload by previewing and selecting thumbnails?

can HTTP POST do client side automatic photo resizing so that we don't need to upload 2mb per photo?

---

### Post by wolfie2x on 2008-07-29
> **stevoo said:**
> 
But they are using mostly flash stuff and as flush is a bit buggy .... well it is causing the crash !

true flash is still buggy and crashes a lot; but on facebook it's mostly AJAX and not flash(except for ads) I think.. and the photo uploader is definitely not flash but a java applet.

---

### Post by wolfie2x on 2008-08-31
finally this seems to be fixed with a SunJava6 update.

working combination:
firefox: 
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

Java JRE:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

Java firefox plugin:
Java(TM) Plug-in 1.6.0_07-b06

( system fully up-to-date as of 31-Aug-08 )

---

