---
title: "How to install JRE?"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Ashfaqur Rahman on 2013-04-14
I have downloaded the tarball file of jre7u17 from java.com.
I cant understand how can i install that!

---

### Post by Paqman on 2013-04-14
You generally don't want to go anywhere near tarballs. On Linux the best way to install software is not the Windows way (go to a website and download something), just open up Ubuntu Software Centre and search for it. This will install straight from the central Ubuntu repositories. This way is far easier and better for a lot of reasons.

For Java you have the option of the official Oracle Java, or the open source implementation of Java called OpenJDK. Personally I'd go with OpenJDK to start, since even the official Java is based of it these days anyway.

---

### Post by ajgreeny on 2013-04-14
> **Paqman said:**
> You generally don't want to go anywhere near tarballs. On Linux the best way to install software is not the Windows way (go to a website and download something), just open up Ubuntu Software Centre and search for it. This will install straight from the central Ubuntu repositories. This way is far easier and better for a lot of reasons.

For Java you have the option of the official Oracle Java, or the open source implementation of Java called OpenJDK. Personally I'd go with OpenJDK to start, since even the official Java is based of it these days anyway.

+1
I've been using openjdk-7-jre for a long time now and have never had any problems with it.  Originally my bank's website needed Sun (now Oracle) java to work, but not any longer.

---

### Post by QIII on 2013-04-14
If you really need Oracle Java 7, please see the link in my signature. Under Oracle Java 7, Command Line Methods, find "Using webupd8.org's strikingly simple method"

But if you don't absolutely need it, you can just go with OpenJDK.

---

### Post by Ashfaqur Rahman on 2013-04-17
Actually I need JVM to use jdownloader.
I have already downloaded jre7u17 from download.java.com.
And follow their following instructions to install that:



[LIST=1]
[*]**Change to the directory in which you want to install.** Type:
cd <*directory path name*>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/

**Note about root access:** *To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions*
[*]Move the .tar.gz archive binary to the current directory.
[*]**Unpack the tarball and install Java** 
tar zxvf jre-7u7-linux-i586.tar.gz

The Java files are installed in a directory called jre1.7.0_07 in the current directory. 
In this example, it is installed in the /usr/java/jre1.7.0_07 directory. 
When the installation has completed, you will see the word **Done**."

But It didn't work cause jdownloader still showing:

" [FONT=inherit]No suitable Java Virtual Machine could be found on your system.[/FONT]The version of the JVM must be at least 1.6 and at most 2.0.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file
 "

Is there any way to make that tarball file work?
[/LIST]

---

### Post by Ashfaqur Rahman on 2013-04-17
I have found the solution here........

[http://www.liberiangeek.net/2012/04/install-oracle-java-runtime-jre-7-in-ubuntu-12-04-precise-pangolin/#comment-7516](http://www.liberiangeek.net/2012/04/install-oracle-java-runtime-jre-7-in-ubuntu-12-04-precise-pangolin/#comment-7516)

Thanks everybody for reply. :)

---

