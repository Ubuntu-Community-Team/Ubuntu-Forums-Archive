---
title: "help with installing JDK6"
date: 2007-01-31
forum: Programming Talk
---

### Post by faultedperfection on 2007-01-31
Okay so I am taking a Java Programming class, so naturally I need to install the JDK, but I am having troubles doing this. Also, I do not want to use eclipse as I prefer to hard code everything in a text editor. 

I installed it, but now when I try to javac anything I get an error in the terminal that says the command can not be found.

Anyone have any suggestions?

Thanks

---

### Post by phossal on 2007-01-31
Depending on how you install the JDK, you may just need to export a JAVA_HOME environment variable. There are a lot of ways to solve the problem, but, in a nutshell, what you're trying to do is update your PATH with the path to javac.

---

### Post by steve.horsley on 2007-02-02
I just downloaded the JDK "self extracting executable" from java.sun.com. 
Made it executable: chmod +x filename
Execute it as root: sudo ./filename (it installs into /opt)
Put symlinks to /opt/jdkblah/bin/java and javac into /usr/bin

---

### Post by phossal on 2007-02-02
> **steve.horsley said:**
> Put symlinks to /opt/jdkblah/bin/java and javac into /usr/bin

That's a good idea - one I use myself routinely. Beginners who can't find javac may not know how to set up links either though. I like the advice, but maybe you could write it out step by step so *anyone* could do it.

---

### Post by steve.horsley on 2007-02-03
To make the symlinks, 
sudo su
[B]cd /usr/bin
ln -s /opt/jdk1.6.0/bin/java java
ln -s /opt/jdk1.6.0/bin/javac javac[/B]

---

