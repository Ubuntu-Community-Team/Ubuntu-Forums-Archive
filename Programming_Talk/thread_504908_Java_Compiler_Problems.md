---
title: "Java Compiler Problems"
date: 2007-07-19
forum: Programming Talk
---

### Post by thomasaaron on 2007-07-19
I'm writing a program in Netbeans. Everything was working great. I could run the program from within Netbeans, and outside of Netbeans with:

java -jar <Program Name>.

Then I made a blunder that I can't seem to dig out of.
I downloaded Eclipse and tried to import the project into Eclipse to see if it would be compatible with a Netbeans project.

Now, I can no longer run my program outside of Netbeans. In other words when I type:
java -jar < Program Name >
...I get the following error:


Exception in thread "main" java.lang.ClassFormatError: DashboardGUI (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

Here's what I've done to resolve the problem:

1. I uninstalled Eclipse and everything associated with it (including it's java packages).
2. I uninstalled and re-installed my sun-java software, including netbeans.
3. I deleted everything out of my Netbeans class folder and re-compiled the project.

This still did not work. My program would run within Netbeans, but I get the error message outside of netbeans.

4. Using my old source files, I completely re-created the five classes that comprise my program and re-compiled them.

I still get the same error.

 It seems it's tripping up on the class version. Another post that talks about a similar error says that the Java version has to be smaller than the javac version.

Here are my versions:
java version 1.4.2
javac 1.6.0

Do you guys have any ideas on this?


Best,
Tom

---

### Post by Voynix on 2007-07-19
> **thomasaaron said:**
> 
Exception in thread "main" java.lang.ClassFormatError: DashboardGUI (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)



  Hi Tom, it seems you are not compiling with the JDK 1.6, and the classpath is not set. Which java JDK did you install? Can you type java -version on the console?

---

### Post by thomasaaron on 2007-07-19
> thomasaaron@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)


> thomasaaron@ubuntu:~$ javac -version
javac 1.6.0

From what I've read, that seems to be right.
Also, when I set this up the first time, I did not have to set CLASSPATH.
Is it possible Eclipse hosed something with my CLASSPATH variable?

Best,
Tom

---

### Post by steve.horsley on 2007-07-19
Voynix is right - you are not using the java installation you think you are. I hae found that the easiest way to make sure you are using the right versions of java and javac is to put symlinks in /usr/local/bin to the right places. /usr/local/bin is earlier in the path than /usr/bin, so this overrides the normal paths, that are not necessarily pointing where you want. Here is my one:
> steve@StevesPC:~$ ls -l /usr/local/bin/j*
lrwxrwxrwx 1 root root 24 2007-07-08 00:36 /usr/local/bin/jar -> /opt/jdk1.6.0_02/bin/jar
lrwxrwxrwx 1 root root 25 2007-07-08 00:36 /usr/local/bin/java -> /opt/jdk1.6.0_02/bin/java
lrwxrwxrwx 1 root root 26 2007-07-08 00:36 /usr/local/bin/javac -> /opt/jdk1.6.0_02/bin/javac


---

### Post by Voynix on 2007-07-19
> **thomasaaron said:**
> From what I've read, that seems to be right.
Also, when I set this up the first time, I did not have to set CLASSPATH.
Is it possible Eclipse hosed something with my CLASSPATH variable?

Best,
Tom

It is a classpath problem. You are not compiling with jdk 1.6 but the gnu libraries. 

```
[FONT=Verdana][SIZE=1][SIZE=2]update-alternatives --config java[/SIZE][/SIZE][/FONT]
```

Choose the sun jdk and everything should be ok.

---

### Post by thomasaaron on 2007-07-19
Well, you guys are absolutely correct.
Thank you kindly. I'm back up and running.

But how did that happen?
Since everything was working perfectly BEFORE eclipse, can I assume that eclipse modified that configuration for its own purposes?

I've never seen that command before, by the way. I'm glad you knew it.
That's not one I would've stumbled upon.

Best,
Tom

---

### Post by Voynix on 2007-07-19
Hi Tom,

I am glad everything is working now. My guess is that you are installing eclipse and netbeans from the repos... Since I install all my java applications manually I can only suspect the installation modified the classpath. 

Cheers and happy coding,

---

### Post by thomasaaron on 2007-07-20
Yep. That is what I did.

Much appreciation.
Best,
Tom

---

### Post by mahboop on 2009-01-15
[COLOR="Green"][B]Hi guys, 

I was having the same problem
but with the help of your instructions
the problem is solved now

Thanks All
I really appreciate your work[/B][/COLOR]

---

