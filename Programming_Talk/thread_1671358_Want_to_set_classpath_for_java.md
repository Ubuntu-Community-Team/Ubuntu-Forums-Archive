---
title: "Want to set classpath for java"
date: 2011-01-19
forum: Programming Talk
---

### Post by worldblackstar on 2011-01-19
I am new to Linux.  I know how to set classpath in windows but linux.   Please help me for setting the classpath. 

I follow this instruction:
[http://ubuntuforums.org/showthread.php?t=1113039](http://ubuntuforums.org/showthread.php?t=1113039)
But it doesn't work.  It showing No such directory

My javafolder is in "usr/local" 
folder name: "jdk1.6.0_23"


It is showing "usr/local/jdk1.6.0_23/bin/java" no such a directory

---

### Post by dileepm on 2011-01-27
To run a simple java program that makes use of builtin APIs you need not set the class path. Ignoring the version of your Ubuntu you may have to do this.

If you have java folder as '/usr/local/java'

In '/etc/environment' file say this

> JAVA_HOME=/usr/local/java
PATH=whatever_earlier:/usr/local/java/bin

---

