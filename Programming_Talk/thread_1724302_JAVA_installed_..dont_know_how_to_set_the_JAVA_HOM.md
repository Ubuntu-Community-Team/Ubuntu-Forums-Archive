---
title: "JAVA installed ..dont know how to set the JAVA_HOME and CLASSPATH"
date: 2011-04-08
forum: Programming Talk
---

### Post by keerth516 on 2011-04-08
Hi,

I have installed the sun-java6 using apt-get install.
it got interrupted and aked me to configure it.so i used sudo apt-get -f install to complete the installation.it shoed the correct version of java by using java -version
$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)
 i got that java installed properly.but getting confusion while setting the environment variable and class path..i gooled about 2hrs but nothing worked.please tell me the step by step process of setting the java_home,class path.
 right now java is in this location:
/usr/lib/jvm/java-1.6.0-openjdk.

thanks in advance!!

---

### Post by GregBrannon on 2011-04-08
Here's an [article]("http://download.oracle.com/javase/tutorial/essential/environment/paths.html") you may find useful.

Those environment settings are usually more of a concern in the Windows world.  I've been running Java just fine in Linux without worrying about them.  Do you have a problem you're trying to solve by setting them?  Maybe if you describe the problem, we can suggest a solution.

---

### Post by deathadder on 2011-04-08
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath](http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath)

---

### Post by r-senior on 2011-04-08
> **GregBrannon said:**
> I've been running Java just fine in Linux without worrying about them.
+1

I can't remember the last time I set these things.

---

### Post by DarkHackerX on 2011-04-29
If you really want(need) to set these environment variables, you can always set them in the .bashrc file.

[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=-1]**JAVA_HOME="/usr/java/..."**[/SIZE][/FONT]

---

