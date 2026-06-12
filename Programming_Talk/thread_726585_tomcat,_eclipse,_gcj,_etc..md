---
title: "tomcat, eclipse, gcj, etc."
date: 2008-03-16
forum: Programming Talk
---

### Post by liniaal on 2008-03-16
For school, we are now learning "enterprise java applications", and in this course we are encouraged to use eclipse, with tomcat, and the tomcat plugin. Okay so i have managed to manually run 1 'hello world' jsp file through tomcat. But now i want tomcat to launch from out eclipse, to serve different pages et cetera. I figured, as my school (of course, too strong ties with MS) only documents the installation under windows, that this would be very doable on my ubuntu install. But my laptop refuses it as hard as my PC does.. First of all, with a default eclipse from APT, if i start a 'dynamic web project' eclipse crashes. After i restart it, import the project to the workspace, and edit the index.jsp file, i cannot seem to run the file 'on server' because it will say something like:
"The selection is not within a valid module."
This will still happen after i install tomcat simply out of the .tar.gz to a subdir of my home, ~/opt/tomcat, which was a tip in another thread. This install method seems logical because in other cases, eclipse won't be able to modify conf files. Now, with the tomcat plugin button i can start tomcat most of the times, but if any, it will only serve the normal tomcat "just installed" pages. and not my page. Sometimes eclipse just crashes after a file/save action on a gcj related exception.
Does anyone have, or is anyone able to make, some kind of "howto" for installing eclipse with tomcat and this plugin under Ubuntu? Because i am now going almost as crazy as just switching my laptop back to windows for my project, which would seriously suck unneededly hard.
[SIZE="1"]Ok. I am right now going crazy. I do not understand a bit of my situation. I've been trying to hack this setup together for days now with zero effect.
[/SIZE]


And as a second question, if i do not have too much problems with java and javac being from Sun and non-free, is there a way for me in ubuntu to say that gcj must never be used? Because i've had more problems with that (RMI).

---

### Post by jespdj on 2008-03-17
Do not use gcj (which is an obsolete, slow and incomplete version of Java which is unfortunately the default Java in Ubuntu).

Install Sun Java 6 instead:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
Then try "java -version". If Sun Java 6 isn't being used, then use the following command:
```
sudo update-alternatives --config java
```
and select Sun Java 6 from the list that you'll see.

---

### Post by liniaal on 2008-03-17
i believe all that is already so! :(

```

[*]> java -version                                                     <[~]-[1]
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

[*]> sudo update-alternatives --config java                            <[~]-[0]

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

[*]>                                                                   <[~]-[0]

```
(what is mixed mode?)

---

