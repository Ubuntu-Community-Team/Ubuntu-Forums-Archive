---
title: "problem running a compiled Java program"
date: 2007-05-17
forum: Programming Talk
---

### Post by spearfish on 2007-05-17
Hi,

I recently installed Java on my system, and I am having a problem related to my "CLASSPATH". The system seems to choke on any Java class that I run, after it compiles. For example, if I write a Java class called "welcome", then compile it and run it:

>java welcome
Exception in thread "main" java.lang.ClassFormatError: welcome (unrecognized class file version)
at java.lang.VMClassLoader.defineClass(libgcj.so.7)
at java.lang.Classloader.defineClass(libgcj.so.7)
...
at gnu.java.lang.MainThread.run(libgcj.so.7)

My Java book says something about setting the CLASSPATH when this error occurs, but nothing I have tried seems to work. (sigh) How do you set the "classpath"?

-A

---

### Post by laxmanb on 2007-05-17
How have you installed Java? The virtual machine on your computer is gcj(not sun java)...

 If you're compiling with Sun Java, problems may result esp. as gcj is somewhere around 1.4.2 as far as the version number goes...

btw, you do not have a  CLASSPATH Problem!!

---

### Post by spearfish on 2007-05-17
Hi,

I went to the downloads page at the Sun web site and got the 62 mb JDK install file for Linux.  (The Linux self-extracting file, jdk-6u1-linux-i586.bin)  I followed the install instructions, and installed the Java directory in my /home/user folder.  I set the .bashrc file so that the PATH works.  So, I can type javac prog.java and compile something.  However, if I run the class I just compiled, it has an error.

thanks!

---

### Post by laxmanb on 2007-05-17
Here's what you didn't do: change the default Java VM

Adjust the alternatives to work correctly using [B]update-alternatives
[/B]

I'm not very good with update-alternatives, so do a google search for instructions!

use javac -version
and java -version to make sure Sun JVM is set up....

Best of luck!!

---

