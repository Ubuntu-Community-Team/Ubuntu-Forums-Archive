---
title: "Can't get my shell to work"
date: 2008-04-22
forum: Programming Talk
---

### Post by Unskilled on 2008-04-22
Hi!

I have an assignment from my school to build a shell. But i can't get to run the shell.sh file.

Here is the error:

[email]frank@Frank:~/Skrivbord/lab1.linu[/email]x$ ./shell.sh
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/frank/Skrivbord/lab1.linux/lib/libJavaReadline.so: libtermcap.so.2: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.gnu.readline.Readline.load(Readline.java:133)
        at Shell.main(Shell.java:15)
[email]frank@Frank:~/Skrivbord/lab1.linu[/email]x$ 

It seems that it can't find libJavaReadline, but it is there so why can't it find it?
I probably should mention that i'm a noob :P, i just installed ubuntu for the first time in my life :P
Please help me.

---

### Post by ghostdog74 on 2008-04-22
show your shell.sh file.

---

### Post by Unskilled on 2008-04-22
Here is what is in the shell.sh file:

#!/bin/bash

(export CLASSPATH=lib/:lib/libreadline-java.jar:$CLASSPATH; export LD_LIBRARY_PATH=lib/:$LD_LIBRARY_PATH; java Shell)

---

### Post by ghostdog74 on 2008-04-22
how about your JAVA_HOME? also , make sure you input the correct path for libreadline-java.jar. If it is in /usr/lib/java/lib/libreadline-java.jar for example, then input the whole path in CLASSPATH, not lib/libreadline-java.jar

---

### Post by Unskilled on 2008-04-22
Now my shell.sh looks like this:

#!/bin/bash

(export CLASSPATH=lib/:~/Skrivbord/lab1.linux/lib/libreadline-java.jar:$CLASSPATH;export JAVA_HOME=/usr/lib/jvm/java-6-sun/bin/:$JAVA_HOME;export LD_LIBRARY_PATH=lib/:~/Skrivbord/lab1.linux/lib/:$LD_LIBRARY_PATH; java Shell)

and i get the same exception.

Did i do it right?

---

### Post by stroyan on 2008-04-22
The error message actually says that libJavaReadline.so depends on libtermcap.so.2.
It is libtermcap.so.2 that can't be found by the dynamic loader.
I can't find that library on an ubuntu system either, even using
"apt-file search libtermcap.so.2".

---

