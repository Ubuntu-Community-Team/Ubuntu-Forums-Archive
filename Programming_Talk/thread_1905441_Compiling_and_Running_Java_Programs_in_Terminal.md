---
title: "Compiling and Running Java Programs in Terminal"
date: 2012-01-06
forum: Programming Talk
---

### Post by mouse- on 2012-01-06
I was learning how to program before I switched to Ubuntu, and as I was using Java for a class I learned how to do all things Java-related in Dr. Java.  I probably could install the windows version of this program and run it with WINE, but I was hoping I could perhaps figure out how to compile/run Java programs using the terminal.  However, all of my attempts in doing so have been unsuccessful.  Is there a chance anyone could explain what commands and/or packages are required to compile and run programs using terminal?  Additionally, is it possible to set the classpath using terminal, and if so, how?

---

### Post by KdotJ on 2012-01-06
You can install the open Java JDK by opening a terminal and running:

```
sudo apt-get install openjdk-6-jdk
```

this will also setup the classpath for you. Now you can simple compile and run you java source with the normal javac / java commands. Lets assume your file is called Myprog.java (with the class called Myprog) and is in your home folder... you can compile with:

```
 javac Myprog.java
```

Then run it with:

```
 java Myprog
```

---

### Post by mouse- on 2012-01-06
> **KdotJ said:**
> You can install the open Java JDK by opening a terminal and running:

```
sudo apt-get install openjdk-6-jdk
```this will also setup the classpath for you. Now you can simple compile and run you java source with the normal javac / java commands. Lets assume your file is called Myprog.java (with the class called Myprog) and is in your home folder... you can compile with:

```
 javac Myprog.java
```Then run it with:

```
 java Myprog
```
I appreciate your help, but I have already installed openjdk-6-jdk.  I appreciate the assistance with the compiler command as well {my computer now attempts to compile the program}, but I need to connect my Java program to a number of classes in a .jar file to run them and I have not yet found a means by which I can set the classpath without error messages.

---

### Post by KdotJ on 2012-01-07
Hey, sorry for the quick reply I was doing it on my phone. So what are the issues you are having? You can compile java source files from the command line but you need to compile and run them with links to jars?

You can compile with the class path like this (assuming again you're in the correct directory):

```
javac -cp /path/to/file.jar Myprog.java
```

If you have multiple classpaths, and/or in separate locations you can separate them with a colon... such as:

```
javac -cp /path/to/file1.jar:/path/to/file2.jar Myprog.java
```

Once compiled, you can run the java program while including the classpath:

```
java -cp /path/to/file.jar Myprog
```

---

### Post by mouse- on 2012-01-07
I tried to set the classpath as instructed; however the program still didn't run.  I got a very long list of error messages because the class wasn't recognized {and therefore neither were its methods}.

---

### Post by KdotJ on 2012-01-07
Is the class (or classes) you're trying to compile and run in a package? Are you in the correct folder etc? If possible, can you post the error output you get? (Of course only if you're OK with showing the class names etc)

---

### Post by pbrane on 2012-01-07
if you are trying to create a jar file from multiple .java files then try 

```

javac *.java MyProg

```
from the directory containing the java files.

For more complex programs I'd suggest an IDE like Eclipse or NetBeans.

EDIT: I looked up DrJava and it's a java program. You could just download the jar and run it in Ubuntu from the terminal or create a menu item to run it for you.
I ran it on my computer with
```

java -jar drjava-stable-20100913-r5387.jar

```

---

### Post by mouse- on 2012-01-20
Thanks!

---

### Post by nalin4linux77 on 2012-05-08
:guitar:Thanks
 Now i can do it from my console with NANO + JAVAC :lolflag:
No need for GUI :popcorn:

---

### Post by Naveedch on 2013-01-30
> **KdotJ said:**
> You can install the open Java JDK by opening a terminal and running:

```
sudo apt-get install openjdk-6-jdk
```

this will also setup the classpath for you. Now you can simple compile and run you java source with the normal javac / java commands. Lets assume your file is called Myprog.java (with the class called Myprog) and is in your home folder... you can compile with:

```
 javac Myprog.java
```

Then run it with:

```
 java Myprog
```

Thank you! Works great!!!!!

---

### Post by r-senior on 2013-01-31
This is the danger of old threads. Oracle JDK 1.6 will cease to get security updates from February 2013 and OpenJDK 6 will most likely follow soon after.

Unless you have a compelling need to support a legacy system, install and use OpenJDK 7. 

```
sudo apt-get install openjdk-7-jdk
```

Also watch out for the release of Java 1.8 due later this year.

---

### Post by slickymaster on 2013-01-31
> **r-senior said:**
> This is the danger of old threads. Oracle JDK 1.6 will cease to get security updates from February 2013 and OpenJDK 6 will most likely follow soon after.

Unless you have a compelling need to support a legacy system, install and use OpenJDK 7. 

```
sudo apt-get install openjdk-7-jdk
```

Also watch out for the release of Java 1.8 due later this year.

Absolutely right. [Oracle Java SE Support Roadmap]("http://www.oracle.com/technetwork/java/eol-135779.html") indicates that after February 2013, Oracle will no longer post updates of Java SE 6 to its public download sites. Existing Java SE 6 downloads already posted as of February 2013 will remain accessible in the [Java Archive]("http://www.oracle.com/technetwork/java/javase/archive-139210.html") on Oracle Technology Network. Developers and end-users are encouraged to update to more recent Java SE versions that remain available for public download.

---

### Post by KdotJ on 2013-01-31
While this is true, it all depends on what you're doing. Many companies will stay on Java 6 for a long time. If you start writing code for Java 7, some of it will not compile on Java 6 due to new language features.

---

### Post by r-senior on 2013-01-31
That's true, and some places are even further behind. There is the -source option on javac though and the Maven compiler plugin accepts a similar parameter.

```
javac -source 1.6 MyOldClass.java
```

---

### Post by KdotJ on 2013-01-31
Good old maven lol. Its just like the python 2.x vs 3 problem... but people will eventually catch up.

---

