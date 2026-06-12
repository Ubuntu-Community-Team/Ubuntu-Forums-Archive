---
title: "compiling java files in a shell script"
date: 2009-05-05
forum: Programming Talk
---

### Post by 10ghost on 2009-05-05
[FONT="Arial"]hi readers
i wrote a bash script to compile some java files but it complains on execution it complains about the javac command
this is the shell script[/FONT]

[COLOR="Blue"][SIZE="3"][FONT="Courier New"]#! /bin/sh
#change directory to a commom point of intersection
cd /home/john/Desktop/Olaleke/oladele/ImageApplet2/src/com/gallery/server

javac -d /home/john/Desktop/Olaleke/oladele/ImageApplet2/classes /home/john/Desktop/Olaleke/oladele/ImageApplet2/src/com/gallery/client/PhotoApplet1.java[/FONT][/SIZE][/COLOR]

then it gave me this error message

.[FONT="Courier New"][COLOR="Blue"][SIZE="3"]/ImageAppletCompilation.sh: 5: javac: not found
[/SIZE][/COLOR][/FONT]

what could be the problem wth this script

---

### Post by dwhitney67 on 2009-05-05
The JDK (Java Development Kit) is either installed on your system, or it is not.

Verify this by running:
```

which javac

```

If it is not found, then it would seem that you need to install the JDK!

---

### Post by 10ghost on 2009-05-05
thanks reader
but i have been running java code manually and javac and java have been working properly.
i have actually installed jdk on my system a long time ago.

---

### Post by Arndt on 2009-05-05
> **10ghost said:**
> thanks reader
but i have been running java code manually and javac and java have been working properly.
i have actually installed jdk on my system a long time ago.

Let your script output the value of $PATH and of "whereis javac". Do the same in the interactive shell where you do find 'javac'.

---

### Post by salvachn on 2009-05-06
Add java directory to your PATH variable:
export JAVA_HOME= <java install directory>
PATH=$JAVA_HOME/bin:$PATH

Then check it using echo $PATH. It should contain your java home directory.

---

