---
title: "trouble with make/javac in ubuntu"
date: 2008-10-01
forum: Programming Talk
---

### Post by lordfantas on 2008-10-01
Hi I am fairly new to ubuntu and linux in general. I've used both redhat and ubuntu linux but for the first time I am trying to configure my own ubuntu system. Anyway, lets get to the point. I've been working with some other students on a Java project for the past few months. I've managed to get subversion working, but I can't seem to get make to compile the code. When I run 'make jar' I get the following:

make: /bin/javac: Command not found
make: *** [class/AbstractPlugin.class] Error 127

I figure I have a problem with javac, but I really have no idea how to resolve it. I'd greatly appreciate any help.

---

### Post by dwhitney67 on 2008-10-02
Thanks for attaching the Makefile... oh, wait you didn't!

On my system (Ubuntu that is), javac is in /usr/bin.

---

### Post by lordfantas on 2008-10-02
The problem isn't with the makefile. The trouble is that I'm a newbie and don't know how to configure everything correctly. javac is where its supposed to be, whereis javac returns /usr/bin/javac.

---

### Post by dwhitney67 on 2008-10-02
> **lordfantas said:**
> Hi I am fairly new to ubuntu and linux in general. I've used both redhat and ubuntu linux but for the first time I am trying to configure my own ubuntu system. Anyway, lets get to the point. I've been working with some other students on a Java project for the past few months. I've managed to get subversion working, but I can't seem to get make to compile the code. When I run 'make jar' I get the following:

make: /bin/javac: Command not found
make: *** [class/AbstractPlugin.class] Error 127

I figure I have a problem with javac, but I really have no idea how to resolve it. I'd greatly appreciate any help.

Ok, let's look at the OP again.  Can you explain this statement:
```
make: /bin/javac: Command not found
```
If your javac is in /usr/bin (you've confirmed that), then why does your Makefile seem to think it is in /bin??

You stated that your Makefile is a-ok, but I tend to believe otherwise.

---

### Post by lordfantas on 2008-10-02
Here you go.

---

### Post by dwhitney67 on 2008-10-02
I glanced at your Makefile for about 2 seconds.

Check your environment... what is JAVA_HOME set to?
```
env | grep JAVA_HOME
```
I wager that it is not set.

I would recommend that in lieu of defining JAVA_HOME to be "/usr", that you modify the Makefile to depend on finding 'javac' based on your PATH setting.  In other words, define JAVAC=javac.

If you want to go about solving the problem without modifying the Makefile, then either define JAVA_HOME as an environment variable in ~/.bashrc, or pass it to the Makefile when performing a 'make'.

For the ~/.bashrc choice:
```
export JAVA_HOME=/usr
```

For the command-line choice:
```
JAVA_HOME=/usr make
```

P.S.  Upon reflecting on my answer above, probably the ~/.bashrc option is the best.  However I will let you decide.  Is your code/Makefile going to be ported to other platforms?

P.S.S.  JAVA_HOME really should be set to the root-directory where both javac and java are present.  Thus set JAVA_HOME=/usr/bin (in ~/.bashrc) and modify your Makefile accordingly to remove the "bin" after the JAVA_HOME variable.  Thus the Makefile should have JAVAC=$(JAVA_HOME)/javac.  Ditto for the JAR definition.

---

### Post by lordfantas on 2008-10-02
Yup, JAVA_HOME wasn't set. As there are others who use this same Makefile, I'm not going to monkey with it and go with option A. However, when I close the terminal and open another one, it seems that I have to 'export JAVA_HOME=/usr' again. How can I set that permanently?

---

### Post by dwhitney67 on 2008-10-02
Slap (insert) the export statement into your ~/.bashrc file (and of course, save the file).  Each time you open a terminal (or login again), it will be defined.

---

