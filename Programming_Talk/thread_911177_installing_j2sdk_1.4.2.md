---
title: "installing j2sdk 1.4.2"
date: 2008-09-05
forum: Programming Talk
---

### Post by mlilien on 2008-09-05
I'm trying to install the java 2 sdk.  I downloaded the binaries and created the rpm.  When I run "rpm -iv j2sdk-1_4_2_18-linux-i586.rpm," I get this output:

error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by j2sdk-1.4.2_18-fcs.i586
        sh-utils >= 2.0-1 is needed by j2sdk-1.4.2_18-fcs.i586
        fileutils >= 4.0-8 is needed by j2sdk-1.4.2_18-fcs.i586
        gawk >= 3.0.4-1 is needed by j2sdk-1.4.2_18-fcs.i586
        textutils >= 2.0-2 is needed by j2sdk-1.4.2_18-fcs.i586
        /bin/sh is needed by j2sdk-1.4.2_18-fcs.i586

How do I check to see what versions of each of those I have, and if I don't have them, what's the best place to get them?  I checked synaptic for some, but didn't find them.

Alternatively, is this the best way to install the SDK?

Thanks

---

### Post by Zugzwang on 2008-09-05
Erm, what's wrong with the Ubuntu package management? Look into the Stickies to learn how to install it using the regular Ubuntu package management. And then you'll get version 6 instead of the outdated 1.4.2.

---

### Post by jespdj on 2008-09-05
> **mlilien said:**
> Alternatively, is this the best way to install the SDK?
No. You should always prefer Ubuntu's package management system before trying to install software manually.

Is there a reason why you want to install the outdated Java version 1.4.2? It's better to install the latest Java version, which is version 6. Note that Sun Java 6 is backward compatible with 1.4.2; anything that runs on 1.4.2 will also run on Java 6.

If you really have a special reason to install Sun Java 1.4.2: Ubuntu works with .deb (Debian) packages. RPM is the native package management system of Red Hat (Fedora) and a number of other Linux distributions. The program named "alien" can be used to convert RPM to DEB packages that can be installed on Ubuntu.

---

### Post by mlilien on 2008-09-05
Ok, I guess I already had that installed.  I'm trying to build Sphinx, a java speech recognizer.  The install instructions say 1.4.2 is the latest version, I just hadn't checked to see how recently the installation instructions were written.

In that case, my question is now, I need to set JAVA_HOME and ANT_HOME in order to build Sphinx.  Do you know what I need to set these to for java 6?

---

### Post by HotCupOfJava on 2008-09-05
Well, this may be easier than you think......

Make sure you have the latest version of Sphinx - you may be using an older version, what what I can tell. Look here:

 [http://cmusphinx.sourceforge.net/sphinx4/](http://cmusphinx.sourceforge.net/sphinx4/)

Since you are trying to build it, I am assuming you have downloaded source code. You can certainly go that way, but from what I can tell of the website, there is an already-built .jar file version available, in which case all you would need is the Java Runtime Environment (JRE), not the Java Development Kit (JDK). You could then simply change to the directory Sphinx is in, type "java -jar <filename>.jar" and run it. 

You can of course get either the JRE or the JDK from Sun using Synaptic Package Manager (assuming you are using Ubuntu or some variant). Synaptic will help make sure you have everything installed that you would need. The JRE is labeled "sun-java6-jre" and the JDK "sun-java6-jdk" under Synaptic. Just do a search in it for "sun java" and you will see them. You can even install ant this way (its called "ant":) ). 

hope this helps

---

### Post by HotCupOfJava on 2008-09-05
I notice that you will also need the JSAPI package to run Sphinx. These are speech-related libraries for java. I do not think they come standard with the JRE or JDK for Java. You may have to follow the instructions for installing these libraries as well ([http://cmusphinx.sourceforge.net/sphinx4/doc/jsapi_setup.html](http://cmusphinx.sourceforge.net/sphinx4/doc/jsapi_setup.html)), if they are not provided in the Sphinx .jar files. Unfortunately, you can't get them through Synaptic.

---

### Post by mlilien on 2008-09-05
I'm downloading the source files because I'm going to do some development with it.  I'm using the sphinx 4.1 beta.  I'll try the nightly builds tomorrow, but I think I'll have the same problem.  The instructions say that I need to set JAVA_HOME and ANT_HOME, but it doesn't say what I need to set them to, so when I try to build it with ant now, I get the following:

BUILD FAILED
/home/mark/programming/sphinx_plus/sphinx4-1.0beta/build.xml:226: The following error occurred while executing this line:
/home/mark/programming/sphinx_plus/sphinx4-1.0beta/build.xml:251: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-sun-1.6.0.06/jre"


As far as the JASPI goes, it does come with it.

---

### Post by jespdj on 2008-09-06
Did you install the **JDK** (Java Development Kit, which includes the Java compiler and other development tools), or the **JRE** (Java Runtime Environment, which does not include development tools)?

Make sure you install the JDK:
```
sudo apt-get install sun-java6-jdk
```
You must also install Ant, which is a build tool similar to 'make':
```
sudo apt-get install ant
```
You can set environment variables such as JAVA_HOME and ANT_HOME like this:
```
export JAVA_HOME=/usr/lib/jvm/java-6-sun
export ANT_HOME=/usr/share/ant
```
You can put those two commands in your /home/username/.profile if you want to make them permanent.

---

### Post by mlilien on 2008-09-06
Thanks, that worked perfectly

---

### Post by cdaver on 2009-12-07
Hi All,

There may be a valid reason to install J2SDK 1.4 onto recent distributions of ubuntu.  For example your code will only compile with 1.4.
If that is the case and you can accept the fact that 1.4 is EOL'ed then here is what you do.

Download J2SDK1.4 from the [sun archives]("http://java.sun.com/products/archive/j2se/1.4.2_19/index.html").

I would suggest downloading the *.bin file.

Once the file is downloaded:
Move it into your JVM root directory, mine is located in /usr/lib/jvm so that is what I will use as an example.
mv download/downloaded_file_name /usr/lib/jvm/downloaded_file_name
cd /usr/lib/jvm
chmox +x <downloaded_file_name> or simpler yet chmod +x *.bin
./<downloaded_file_name>.bin

You have now successfully have the J2SDK-1.4 folder. 

From this point on you can do many things, make it your default JVM using update-java-alternatives, point eclipse to it, point maven to it, set env variables for JAVA_1.4_HOME, etc.

Thanks for reading.

---

### Post by jespdj on 2009-12-08
> **cdaver said:**
> There may be a valid reason to install J2SDK 1.4 onto recent distributions of ubuntu.  For example your code will only compile with 1.4.
If you have Java source code that only compiles with JDK 1.4, then you have a badly written Java program. Sun treats backward compatibility as the most holy thing in the world, and any old Java source code should compile with the latest Java version with no problems. You'd be better off to fix your broken source code instead of installing an old Java version.

---

### Post by pulkittomar on 2011-02-22
> **cdaver said:**
> Hi All,

There may be a valid reason to install J2SDK 1.4 onto recent distributions of ubuntu.  For example your code will only compile with 1.4.
If that is the case and you can accept the fact that 1.4 is EOL'ed then here is what you do.

Download J2SDK1.4 from the [sun archives]("http://java.sun.com/products/archive/j2se/1.4.2_19/index.html").

I would suggest downloading the *.bin file.

Once the file is downloaded:
Move it into your JVM root directory, mine is located in /usr/lib/jvm so that is what I will use as an example.
mv download/downloaded_file_name /usr/lib/jvm/downloaded_file_name
cd /usr/lib/jvm
chmox +x <downloaded_file_name> or simpler yet chmod +x *.bin
./<downloaded_file_name>.bin

You have now successfully have the J2SDK-1.4 folder. 

From this point on you can do many things, make it your default JVM using update-java-alternatives, point eclipse to it, point maven to it, set env variables for JAVA_1.4_HOME, etc.

Thanks for reading.

Thank you very much. I really needed java sdk 1.4 to run some tools which work on verification of java program and built with support features in java 1.4.

---

