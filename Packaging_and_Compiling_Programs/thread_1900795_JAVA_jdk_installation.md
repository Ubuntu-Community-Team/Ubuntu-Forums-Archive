---
title: "JAVA jdk installation"
date: 2011-12-27
forum: Packaging and Compiling Programs
---

### Post by sagarjojo on 2011-12-27
I was trying to install jdk kit. I tried with "$ sudo apt-get install sun-java6" this, then i get a screen that contains the Sun__[[COLOR=#95181C][/COLOR][COLOR=#95181C][/COLOR]]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html#") Operating System Distributor License for Java and <ok> text but I am unable to click on that and hitting enter is not also working. I am attaching the screen shot, please someone help me, i am getting frustration............](*,)

---

### Post by shkelzen on 2011-12-27
[http://www.fudzilla.com/home/item/25261-ubuntu-kills-java](http://www.fudzilla.com/home/item/25261-ubuntu-kills-java)

---

### Post by QIII on 2011-12-27
Per previous post, Sun Java is no longer in Canonical's repos.  You will have to install by another method.  Whether you agree or disagree with either Oracle's or Canonical's moves, you will have to simply accept the current situation.  Besides, the Update 26 that was in the repos is full of security problems.  You want Java Update 30 (and the same for the JDK) unless you want Java 7 -- which I would not recommend unless you want to do some bleeding edge experimentation.

First, uninstall any current version of Sun Java and then go here and install the JRE following the detailed instructions.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Then, go to Oracle's site and download/install the JDK following the instructions there and make sure you get it into the same directory as the JRE.

OpenJDK is a fine effort.  Unfortunately, the world often does not recognize it as Java.  It will eventually happen, I think.  But you are dealing with the here and now.

---

### Post by 1clue on 2011-12-27
I have never managed to get a Linux-based Java to work in a real development scenario.

Here's what I do:
[LIST=1]
[*]Download the sun jdk from [http://java.sun.com](http://java.sun.com) (which will be redirected to someplace on oracle)
[*]Extract it to /opt/java6/sun/<whatever> where <whatever> is the name of the directory created by the archive.
[*]From /opt/java6 type **ln -s sun/<whatever> current**
[*]Set your JAVA_HOME environment to /opt/java6/current
[*]Edit your PATH environment so that $JAVA_HOME/bin comes before /usr/bin.
[/LIST]

Anything Java-related I use this same scenario.  Groovy, grails, anything.  If you're using Eclipse or STS then show it the non-linked JVM when you're setting up JVMs.

This scenario lets you have multiple java6 installations and switch them as easily as re-linking to some other folder.

You can also have multiple defaults by using **ln -s /opt/java6/<whatever> current_tomcat6** or similar, then set the JAVA_HOME in the script that runs the service in question.

---

### Post by sammiev on 2011-12-27
If you need the latest JRE java then you need to follow [these]("http://sites.google.com/site/easylinuxtipsproject/java") instructions but others may work. Jre java is required from sites like pogo and others. All instructions are very simple and are used by many.

---

### Post by JOHNNYG713 on 2011-12-27
To answer your post, press the "tab" key then "enter"

---

