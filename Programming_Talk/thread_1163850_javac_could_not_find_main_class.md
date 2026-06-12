---
title: "javac: could not find main class"
date: 2009-05-19
forum: Programming Talk
---

### Post by navneeth on 2009-05-19
I think it's pretty self-explanatory. I'm unable to compile Java programs. Kindly help. 

```
navneeth@ubuntu:~$ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Client VM (build 11.3-b02, mixed mode, sharing)
navneeth@ubuntu:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
navneeth@ubuntu:~$ javac -version
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/tools/javac/Main
Caused by: java.lang.ClassNotFoundException: com.sun.tools.javac.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.sun.tools.javac.Main.  Program will exit.

```

---

### Post by MeLight on 2009-05-19
Have you tried simple programs? If you have, please provide the code

---

### Post by Zugzwang on 2009-05-19
A guess: You CLASSPATH environment variable is messed up. Please copy&paste its contents here.

---

### Post by navneeth on 2009-05-19
Oh, yes, I have. 

```
navneeth@ubuntu:~$ cat HelloWorld.java
class HelloWorld
{
    public static void main(String[] args) 
    { 
       System.out.println ("Hello, world!");
    }
}  
navneeth@ubuntu:~$ javac HelloWorld.java
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/tools/javac/Main
Caused by: java.lang.ClassNotFoundException: com.sun.tools.javac.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.sun.tools.javac.Main.  Program will exit.

```

---

### Post by navneeth on 2009-05-19
> **Zugzwang said:**
> A guess: You CLASSPATH environment variable is messed up. Please copy&paste its contents here.

Um, where can I find it? 

The last time I installed Java, which I think was in Gutsy, everything was smooth sailing. This is a fresh install of Jaunty and Java.

---

### Post by navneeth on 2009-05-19
Oh, if you mean echo $CLASSPATH, then it's empty.

---

### Post by jespdj on 2009-05-19
It looks like something is wrong with your JDK installation.

How did you install Sun Java 6; from the repositories, or did you install it manually? Do you have other versions of Java installed?

---

### Post by navneeth on 2009-05-19
From the repos. And no other version of java. 

apt-get install sun-java6-jdk --yes

This error has been reported before, as a Google search will show, but I'm just not able to find a solution.

---

### Post by navneeth on 2009-05-20
Bump.

---

### Post by kpkeerthi on 2009-05-20
In the folder where HelloWorld.java exists, run javac like below:
```

 javac -cp .:$CLASSPATH HelloWorld.java

```

If $CLASSPATH environment variable is set (perhaps in ~/.bashrc it will also be used for the compilation process. It will simply be ignored otherwise.

---

### Post by Zugzwang on 2009-05-20
> **kpkeerthi said:**
> In the folder where HelloWorld.java exists, run javac like below:
```

 javac -cp .:$CLASSPATH HelloWorld.java

```

If $CLASSPATH environment variable is set (perhaps in ~/.bashrc it will also be used for the compilation process. It will simply be ignored otherwise.

That won't help because the java compiling main class itself isn't found.

@OP: Try "sudo update-alternatives --config javac" (the same with "sudo update-alternatives --config java") and see what's up there. Make sure that sun's jvm is also selected as the default one here. It's unlikely that you *only* have the sun jvm installed, as gcj comes piggy-back with a lot of applications.

---

### Post by navneeth on 2009-05-20
> **kpkeerthi said:**
> In the folder where HelloWorld.java exists, run javac like below:
```

 javac -cp .:$CLASSPATH HelloWorld.java

```

If $CLASSPATH environment variable is set (perhaps in ~/.bashrc it will also be used for the compilation process. It will simply be ignored otherwise.

```
navneeth@ubuntu:~$ cat HelloWorld.java
class HelloWorld
{
    public static void main(String[] args) 
    { 
       System.out.println ("Hello, world!");
    }
}  
navneeth@ubuntu:~$ javac -cp .:$CLASSPATH HelloWorld.java
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/tools/javac/Main
Caused by: java.lang.ClassNotFoundException: com.sun.tools.javac.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.sun.tools.javac.Main.  Program will exit.

```

As I said, the CLASSPATH variable comes up empty.

```
navneeth@ubuntu:~$ echo $CLASSPATH

navneeth@ubuntu:~$
```

> **Zugzwang said:**
> That won't help because the java compiling main class itself isn't found.

@OP: Try "sudo update-alternatives --config javac" (the same with "sudo update-alternatives --config java") and see what's up there. Make sure that sun's jvm is also selected as the default one here. It's unlikely that you *only* have the sun jvm installed, as gcj comes piggy-back with a lot of applications.

```
navneeth@ubuntu:~$ sudo update-alternatives --config java
[sudo] password for navneeth: 

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
navneeth@ubuntu:~$ sudo update-alternatives --config javac

There is only 1 program which provides javac
(/usr/lib/jvm/java-6-sun/bin/javac). Nothing to configure.

```

---

