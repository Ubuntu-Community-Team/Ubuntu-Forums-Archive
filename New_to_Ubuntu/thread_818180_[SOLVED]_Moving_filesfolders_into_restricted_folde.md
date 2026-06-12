---
title: "[SOLVED] Moving files/folders into restricted folders"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by AOZ on 2008-06-04
Hey everyone,
I'm not sure how it happened but when i installed JDK 6 it installed onto my desktop. I want to move it to /usr/lib/jvm but it wont let me do it via GUI giving me the error Permission denied. Is there a way to move a folder in the terminal under root? and could someone also please tell me how i can set the JAVA_HOME and CLASSPATH variables.

Thank you in advance for your help

---

### Post by quelx on 2008-06-04
try installing it from **synaptic**, **sun-java6-jdk**

---

### Post by Nessa on 2008-06-04
Try running "gksu nautilus" in the terminal and then try moving the files again thru GUI.

---

### Post by AOZ on 2008-06-04
Thanks Nessa that worked perfectly. I still dont know ohw to set those variables though and im having a world of problems with eclipse because of that. Anyone have an idea?

---

### Post by AOZ on 2008-06-04
Thanks Nessa that worked perfectly. I still dont know ohw to set those variables though and im having a world of problems with eclipse because of that. Anyone have an idea?

---

### Post by NormR2 on 2008-06-04
Enter JAVA_HOME in the Search field(upper right) and you'll get many posts telling you different ways to set that variable.  
Get the current value (in a Terminal window type: echo $JAVA_HOME) to see what is was, then go to one of the places you found with Search and change the path to be to where java is now.

---

### Post by AOZ on 2008-06-04
Thanks alot guys for the quick replies I'll go check out those threads

---

### Post by jamesstansell on 2008-06-05
> **AOZ said:**
> I still dont know ohw to set those variables though and im having a world of problems with eclipse because of that. Anyone have an idea?

You normally shouldn't need to set either JAVA_HOME or CLASSPATH anymore.  A stand-alone Ant install was the only thing I've used in the last 2+ years that required it.

It's normally best to tell eclipse directly where your JVM is.  When eclipse starts the JVM it can automatically read the sytem property if it needs the java home.  The classpath eclipse already manages itself for you.

In these two regards, NetBeans works essentially the same as Eclipse.

Eclipse with Ubuntu 8.04 has been problematic for some people.  Searching for posts tagged with eclipse may of help to you.

---

### Post by jamesstansell on 2008-06-05
> **AOZ said:**
> Thanks Nessa that worked perfectly.

In the future please remember that you have files in a system directory (/usr/lib/jvm) that the system doesn't know about because the Ubuntu install routine wasn't used.  It will probably work fine for you for now, but could cause weird problems in the future.  It also mean you should be conscientious about manually checking for and manually installing the inevitable security updates.

Whenever I need to use a JVM that's not packaged for system installation, I just put in in my ~/opt/java folder.  (I installed the new beta of Java 6 Update 10 this morning that way.)  Any folder you like will generally work, but it's best that it be somewhere under /home (like I did) or under /usr/local is great too.

---

### Post by jamesstansell on 2008-06-05
> **jamesstansell said:**
> You normally shouldn't need to set either JAVA_HOME or CLASSPATH anymore.

Sorry, I didn't mean to imply that you should know how to set them when you need to, or just want to.

I'm not sure what your Java home directory is called, but presumably it is similar to /usr/lib/jvm/jdk_1.6.0_06 - substitute whatever directory you need below.

```
$ export JAVA_HOME=/usr/lib/jvm/jdk_1.6.0_06
```

The CLASS_PATH variable can be set the same way.  Or it can have multiple directories, using CLASS_PATH=dir_one:dir_two:dir_three.  See how a ':' is used to separate the directory paths?

As to what values to use for CLASS_PATH it will differ for each application.  Most already arrange to have it set the way they want it.  If you see a command like "java -cp" the "-cp" part is followed by a classpath, but it's never set in the CLASS_PATH environment variable.

The java command itself tends to ignore JAVA_HOME, curiously enough.

---

