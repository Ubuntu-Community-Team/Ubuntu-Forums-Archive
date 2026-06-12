---
title: "Importing java.util.Scanner not working"
date: 2006-11-26
forum: Programming Talk
---

### Post by mcai6in2 on 2006-11-26
[SIZE="3"]Hi,
**
Can anyone help me?

I've installed the Sun JDK kit via Synaptics.  Simple java programs without importing any libraires compile and run fine.

However, whenever i try to import the above library (java.util.Scanner), the program compiles, but produces a runtime error:

*Exception in thread "main" java.lang.ClassNotFoundException: java.util.Scanner not found in gnu.gcj.runtime.SystemClassLoader..."*

Anybody any ideas?[/SIZE]

---

### Post by bieber on 2006-11-26
You installed the JDK, but javac still runs GCJ by default.  You need to set it so that javac uses Sun's compiler, but I can't remember the command.  I'm sure someone here will be able to recall it offhand.

---

### Post by hod139 on 2006-11-26
See this [howto]("http://ubuntuforums.org/showthread.php?t=201378") for more details, but the basic idea of it:
```
 sudo update-java-alternatives -s java-1.5.0-sun
```Next, edit the JVM configuration file
```
sudo -b gedit /etc/jvm
``` and move the line 
```
/usr/lib/jvm/java-1.5.0-sun
``` to the top.

---

### Post by mcai6in2 on 2006-11-27
That's brilliant.  Got it working by doing the above!

Thanks very much.

---

