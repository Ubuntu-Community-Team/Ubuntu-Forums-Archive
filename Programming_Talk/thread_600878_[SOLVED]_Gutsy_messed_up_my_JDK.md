---
title: "[SOLVED] Gutsy messed up my JDK"
date: 2007-11-02
forum: Programming Talk
---

### Post by IsKall on 2007-11-02
I think gutsy messed up my JDK, not certain but this happend since I upgraded from feisty to gutsy (but I can be misstaken)

I want to start this program but I get this error.

```

brusk@ubuntu:~/.idea/bin$ ./idea.sh 
ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
exec: 61: /bin/java: not found

```

and this is my, sudo update-alternatives --config java

```

*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java

```

and my environment looks like this

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:.:/usr/bin:/sbin:.:/bin:.:/usr/games:.:/home/Adrian/.Apache/db-derby-10.2.1.6-bin/lib/derby.jar:.:/home/Adrian/.Apache/db-derby-10.2.1.6-bin/lib/derbytools.jar:.:/usr/lib/jvm/java-6-sun/jre/bin/java:.:ANT_HOME=/usr/local/ant/bin"
LANG="en_US.UTF-8"
ANT_HOME="ANT_HOME=/usr/local/ant"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.03:."
CLASSPATH="/usr/lib/jvm/java-6-sun-1.6.0.03/bin:."

```

---

### Post by LaRoza on 2007-11-02
Was Java updated?

---

### Post by IsKall on 2007-11-02
never mind, solved it.

---

### Post by LaRoza on 2007-11-02
Mark as solved, and possibly state the solution if others may run into the same problem.

---

### Post by IsKall on 2007-11-02
Yes it was updated, but I had to add this line

```

JDK_HOME="/usr/lib/jvm/java-6-sun-1.6.0.03/"

```

---

### Post by LaRoza on 2007-11-02
Thanks, I upgraded to 7.10 and didn't realize Java might not work. (I haven't used it in a while)

---

### Post by IsKall on 2007-11-02
No problem, I didn't realize it when I tried to start Intellj IDEA and Netbeans today, they both where complaining about the JDK_HOME was not found. 

But thats solved now.

---

### Post by linhtinh321 on 2007-11-05
Hi,
I have NetBeans installed in Ubuntu 7.04 and it worked correctly. However, after upgrading to 7.10, when I run the netbeans file in terminal, it said that : 
"Cannot find java. Please use the --jdkhome switch." 
I guest the problem is similar to this topic. However, I don't know how to deal with it. Please help me.
Thanks a lot.

---

