---
title: "Java issue in debian lenny"
date: 2012-04-25
forum: Programming Talk
---

### Post by Drenriza on 2012-04-25
Hi guys.
 
I have created a small java program (for test) for my lenny system, using netbeans 7.1.1 (and compiled in netbeans on windows)
 
I have the following packages installed
 
ii openjdk-6-jre 6b18-1.8.10-0~lenny2 OpenJDK Java runtime, using Hotspot JIT
ii openjdk-6-jre-headless 6b18-1.8.10-0~lenny2 OpenJDK Java runtime, using Hotspot JIT (hea
ii openjdk-6-jre-lib 6b18-1.8.10-0~lenny2 OpenJDK Java runtime (architecture independe 
 
The default java used is
There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
 
But still i get the following errors when i try and execute the program with java programName
 
Exception in thread "main" java.lang.NoClassDefFoundError: RebootTestScript/jar
Caused by: java.lang.ClassNotFoundException: RebootTestScript.jar
at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
 
Could not find the main class: RebootTestScript.jar. Program will exit.
 
Does this have something to do with i compile it in netbeans on windows and try to run it on a Linux os?
 
Hope someone can help me.
Thanks on advance.

---

### Post by PaulM1985 on 2012-04-25
From your error messages it looks like you are using the "java" command to run an executable Jar file.  Is this correct?

If so, I think you are doing this:
```

java my_prog.jar

```

when you should be doing this:
```

java -jar my_prog.jar

```

The "-jar" command lets java know that you want to run a Jar file.

Paul

---

### Post by Drenriza on 2012-04-25
Hi Paul.

Yes i tried java programName before.

Now i did as you suggested

java -jar programName

And i get these errors

xxx@xxx:~$ java -jar RebootTestScript.jar 

Exception in thread "main" java.lang.UnsupportedClassVersionError: reboottestscript/RebootTestScript : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: reboottestscript.RebootTestScript. Program will exit.

Any thoughts?

Edit. A quick google revealed.

This exception can occur when the source is built targeting a JDK that is not supported by the JDK attempting to run it.

Is this because my openjdk-6-* is older than the jdk i used when writing the program on netbeans? As an example.

---

### Post by PaulM1985 on 2012-04-25
Yes, that is the issue.

Your JRE (which runs your Jar and has the "java" program) must be the same version or newer than the JDK (the thing that builds your Jar).

So your options are to update your JRE if there is one available, or download an older version of the JDK which is compatible with your target JRE and build your application with that.

Paul

---

### Post by Drenriza on 2012-04-25
I tried downloading a older java jdk. [http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u31-download-1501634.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u31-download-1501634.html)
 
But even tho this jdk is older (version 6) i get the same error.
 
How can i see what sub-version of the java JDK the JRE can handle?

---

### Post by PaulM1985 on 2012-04-25
Try:
```

java -version
javac -version

```

These will give you the versions of the JRE and JDK that you have.

Paul

---

### Post by ofnuts on 2012-04-25
> **PaulM1985 said:**
> Try:
```

java -version
javac -version

```These will give you the versions of the JRE and JDK that you have.

Paul
You can tell JavaC to compile for a given JVM release ("-target" parm).

---

### Post by PaulM1985 on 2012-04-25
> **ofnuts said:**
> You can tell JavaC to compile for a given JVM release ("-target" parm).

I didn't know that.   You learn something new everyday. :-)

---

### Post by Drenriza on 2012-04-26
And how can i then use this information
 
```
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)
```
 
To know what JDK i should use when building my program?
 
Thanks on advance.

---

### Post by PaulM1985 on 2012-04-26
From the documentation here:
[http://docs.oracle.com/javase/1.5.0/docs/tooldocs/solaris/javac.html](http://docs.oracle.com/javase/1.5.0/docs/tooldocs/solaris/javac.html)
I would guess at trying:
```

javac -target 6 file.java

```

You can then see which JRE your class files are compiled for by using:
```

javap -verbose file

```
where file is your class file without the class extension.  You can tell the version from the minor/major outputs.  For more information see this link: [http://thiamteck.blogspot.co.uk/2007/11/determine-java-class-file-version.html](http://thiamteck.blogspot.co.uk/2007/11/determine-java-class-file-version.html)

Paul

---

### Post by Drenriza on 2012-04-26
Ow my god im tired of this, why should it be so hard to run a simple program on Linux.
 
If i have the following files (ALL in the same folder)
```
Dal.class Gui.class RebootTestScript.class
```
and i have a librarie called
```
sqljdbc4.jar
```
 
And if i just do
```
java -target 6 file1.class file2.class e.t.c
```
i get 3 separate java files.
 
How can i compile this into a single java program? That i can execute.
 
Thanks on advance.

---

### Post by ofnuts on 2012-04-26
> **Drenriza said:**
> Ow my god im tired of this, why should it be so hard to run a simple program on Linux.
 
If i have the following files (ALL in the same folder)
```
Dal.class Gui.class RebootTestScript.class
```and i have a librarie called
```
sqljdbc4.jar
```And if i just do
```
java -target 6 file1.class file2.class e.t.c
```i get 3 separate java files.
 
How can i compile this into a single java program? That i can execute.
 
Thanks on advance.The difficulty of this has nothing to do with Linux..

To produce a single "executable" file, you put your three class files in a JAR, using the "jar" utility.

The "manifest" file of the jar can tell which class provides the "main()" if you execute the jar with "java -jar" (otherwise use java -cp the.jar nameofclasswithmain).

---

### Post by Drenriza on 2012-04-26
Can you give me an example code of how to merge class files together?

---

### Post by cpatrick08 on 2012-04-26
debian lenny is eol you should upgrade lenny  to squeeze

---

### Post by ofnuts on 2012-04-27
> **Drenriza said:**
> Can you give me an example code of how to merge class files together?Just issue "jar" in a command prompt and you'll be given instructions and examples.

Remember that Java packages are matched by directories in your JAR file, so if you declare a class SomeClass with
```

package  my.little.package;

```
it should end up as "/my/little/package/SomeClass.class" in the JAR.

---

### Post by Drenriza on 2012-04-30
Well i hope you guys can help me with a remaining issue.

I have now created my project in netbeans on mac os x and not windows. Builded it and run it, and the helloWorld program works. So now i can at least run my basic programs on my Lenny system. Even tho i have no idea what the difference is.

The remaining issue is as follows.

I have a .jar file added as a library to my project. And when i build my project this (as far as i know) does not get added to the .jar file that is created containing the different classes.

So naturally when i run my program i get the following error
Exception in thread "main" java.lang.ClassNotFoundException: **_org.postgresql.Driver_**
How can i resolve this issue? Has this something to do that i need to point my classpath towards this .jar file? Or how can i execute MyProgram.jar file with the org.postgresql.driver.jar

Thanks on advance.

---

### Post by PaulM1985 on 2012-04-30
Normally, when you build using Netbeans, your libraries are put in a lib folder in dist.  So if you want to use your program, you copy the entire contents of the dist folder.  Do your libraries get copied into the lib folder?

Paul

---

### Post by Drenriza on 2012-04-30
> **PaulM1985 said:**
> Normally, when you build using Netbeans, your libraries are put in a lib folder in dist. So if you want to use your program, you copy the entire contents of the dist folder. Do your libraries get copied into the lib folder?
 
Paul
 
Yes it creates a dist folder where it places the lib (containing the sql.jar) readme and the myProgram.jar file / files.
 
EDIT.
I copied my dist folder to the system and did as the readme file sayd.
 
To run the project from the command line, go to the dist folder and
type the following: java -jar "test.jar"
 
but when i change directory to the dist folder and type the command
java -jar "test.jar" or java -jar test.jar
 
i get and error saying
Exception in thread "main" java.lang.ClassNotFoundException: org.postgresql.Driver

---

### Post by ofnuts on 2012-04-30
To tell java too look for classes in some defined places, you have to use the -cp parameter (CLASSPATH) followed by a list of jars and/or directories (directories of classes, not of jars). Pointing at a directory there is equivalent  to pointing at  a JAR built by zipping the same directory.

---

### Post by Drenriza on 2012-05-03
> **ofnuts said:**
> To tell java too look for classes in some defined places, you have to use the -cp parameter (CLASSPATH) followed by a list of jars and/or directories (directories of classes, not of jars). Pointing at a directory there is equivalent to pointing at a JAR built by zipping the same directory.
 
So am i using the command correct if i do it as such
 
```
java test.jar -cp lib/sqljdbc4.jar
```
 
The above still gives me a 
Exception in thread "main" java.lang.ClassNotFoundException: org.postgresql.Driver
 
Kind regards.

---

### Post by ofnuts on 2012-05-03
> **Drenriza said:**
> So am i using the command correct if i do it as such
 
```
java test.jar -cp lib/sqljdbc4.jar
```The above still gives me a 
Exception in thread "main" java.lang.ClassNotFoundException: org.postgresql.Driver
 
Kind regards.
With this syntax, you are telling Java to start test.jar, and to pass "-cp" and "lib/sqljdbc4.jar'" as parameters to it. Correct syntax for what you want to do is:
```
java  -jar -cp lib/sqljdbc4.jar test.jar
```

---

### Post by Drenriza on 2012-05-07
Thanks.

I finally got it working.

Kind regards.

---

