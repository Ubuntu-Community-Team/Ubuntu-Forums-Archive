---
title: "[SOLVED] I've set the JAVA_HOME but still cannot run Intellij IDEA"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by drtre on 2008-10-26
Hi everyone,

I had a thread for the same problem 2 days ago but since no one cared :( I thought not to bother with the old thread and create a new one. First of all I have to say that I'm using java-6-openjdk as my JDK.


I believe I've set the JAVA_HOME:

> 
The last lines in my bash.bashrc

export JAVA_HOME="/usr/lib/jvm/java-6-openjdk/"
export CATALINA_HOME="/home/soheil/Programs/apache-tomcat-6.0.14/"
export JDK_HOME="/usr/lib/jvm/java-6-openjdk/"

I've also set the PATH variable for IDEA's /bin:

> 
Lines in /etc/environmet

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/soheil/Programs/idea-7590/bin"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

And run this command:

> source /etc/environment

Also set "/usr/lib/jvm/java-6-openjdk" it in the /etc/jvm as the highest priority JVM. And set it as the default JVM through this:

> update-java-alternatives -s java-6-openjdk

The problem though is, when I try to run idea.sh the following errors come up:

> ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
exec: 61: /bin/java: not found

Please someone help me with this. I really need to run IDEA 'cause I got some work to do. I'm desperate right now ... 

Thanks in advance.

---

### Post by drtre on 2008-10-27
again no help ... ?

---

### Post by jespdj on 2008-10-27
Remove the slashes at the end of the directory names, for example:
```
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
```
instead of
```
export JAVA_HOME="/usr/lib/jvm/java-6-openjdk/"
```

---

### Post by mjparme on 2008-10-27
You aren't reading the error closely enough, it tells you EXACLTY what you need to do.

The error doesn't say anything about setting JAVA_HOME. It says to set JDK_HOME or IDEA_JDK.

Add this to your /etc/environment, I have found you need to logout and log back in for the /etc/environment changes to take effect (sourcing it doesn't work for a GUI app). Set it to the location of your java and with the appropriate version of course.

JDK_HOME=/usr/java/jdk1.6.0_10

---

### Post by drtre on 2008-10-27
I've tested with or without the slashes but no change at all. Also about JDK_HOME and IDEA_JDK you see my bash.bashrc. They're set.

The Thing is when I got Gutsy, I had no problem running it but since I updated it to Hardy I've this problem. I wonder if the problem is 
> exec: 61: /bin/java: not found
in the last line console output.

---

### Post by mjparme on 2008-10-27
Are you trying to start intellij from the command line or a menu item?

If from the command-line please show me the output of this:

env | grep -i JDK


If from a menu item you need to add JDK_HOME declaration to /etc/environment then logout and back in (may have to reboot, but pretty sure just log out an in works, you can't just source it [well you can but it only applies to the terminal you sourced it from])

---

### Post by drtre on 2008-10-28
I'm running from command line. I have this problem for a week and dude believe me I have logged out and in a dozen times but that's just the same :popcorn:. 
I think setting the JAVA_HOME or JDK_HOME in .bashrc file should suffice. BTW sourcing does make the changes permanent. That makes the $PATH variable to pick up the new directory. And here's the env | grep -i JDK output:

> JAVA_HOME=/usr/lib/jvm/java-6-openjdk
JDK_HOME=/usr/lib/jvm/java-6-openjdk

Anything else? And again what about the last line of error ...
I appreciate any IDEA:popcorn:

---

### Post by drtre on 2008-11-16
Thanks for not helping. I guess I have to go back to Windows or at least switch to Eclipse for a while.

---

### Post by Grubbles on 2008-12-21
I don't know if you've solved this issue yet, but from what I've read, you can't use openJDK for IntelliJ.  Try using Sun's JDK.

---

### Post by evaliauka on 2010-10-21
I had a similar problem. 
I'm using sun jdk. After update from version 1.6.0.20 to 1.6.0.22 my IntellIJ IDEA did not want to start and just gave me error:> exec: 61: /usr/lib/jvm/java-6-sun-1.6.0.20: not foundI modified my /etc/environment to accept new version of jdk:
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib"
JRE_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22/jre"
JDK_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"
Previous version was:
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib"
JRE_HOME="/usr/lib/jvm/java-6-sun-1.6.0.20/jre"
JDK_HOME="/usr/lib/jvm/java-6-sun-1.6.0.20"
But "echo $JDK_HOME" was still "/usr/lib/jvm/java-6-sun-1.6.0.20".

I searched for files containing string "JDK_HOME" and found ~/.profile. There was:
> JDK_HOME="/usr/lib/jvm/java-6-sun-1.6.0.20"I do not remember, whether I edited this file myself. But after I removed this line, IDEA works fine :)

---

