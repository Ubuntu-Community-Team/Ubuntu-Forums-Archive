---
title: "How should I set environment variables permanently for JMF?"
date: 2010-02-21
forum: Programming Talk
---

### Post by pedramslhr on 2010-02-21
Hi.
I have downloaded and installed JMF and used following commands to set CLASSPATH and LD_LIBRARY_PATH:

```
export JMFHOME=/home/pedram/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:$CLASSPATH
export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH
```

The problem is I can compile and run programs using for example javax.media after these commands from the same terminal window. but as soon as I close the window I should every thing again or I get such an error:

```
Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/NoPlayerException
```

Thanks!

---

### Post by Simon17 on 2010-02-21
Define the variables in one of your startup scripts?

---

### Post by pedramslhr on 2010-02-22
Thank you for answering.
I added these variables permanently using:
-[https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")
-[https://edge.launchpad.net/ubuntu/+bug/366728]("https://edge.launchpad.net/ubuntu/+bug/366728")
-[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/380360]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/380360")
and I'm able to run my programs using java and javac commands.
But now I'm curious to know how should I import and use JMF classes in my projects in Netbeans.
Thanks!

---

### Post by pedramslhr on 2010-02-23
I add jar files in lib folder and it seems now I can access JMF classes in my project.

---

