---
title: "Running Java Programs from a Terminal"
date: 2010-12-28
forum: Programming Talk
---

### Post by Kuo000 on 2010-12-28
Hi all,

I am just new to Ubuntu (installed it a few days ago alongside my Windows XP laptop). I normally just program Java in Eclipse and never use a terminal to compile and run my Java programs. I tried to compile and run a hello world Java program from a terminal using the GNU compiler for Java (gcj) with the commands:

> javac HelloWorld.java (a HelloWorld.class is created after this command)
> java HelloWorld

But after the "java HelloWorld" command, I got:

Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld (wrong name: main/HelloWorld)
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
Could not find the main class: HelloWorld. Program will exit.

What's wrong with this? I think I do have the Java runtime (JavaSE-1.6 and java-6-openjdk) installed with the installation of Eclipse. My HelloWorld program simply prints a "Hello World" in the console and runs perfect in my Eclipse. Do I need to manually set the classpath for the java runtime for the program to run from a terminal, and if so how???

Thanks very much for any help.

---

### Post by trent.josephsen on 2010-12-28
My Java is rusty, but I do believe that's caused by a faulty package line in the .java file.  "package main;" perhaps?  Delete it and everything should be fine.

---

### Post by Barrucadu on 2010-12-28
Is your class called "HelloWorld"? Show the source code.

---

### Post by Kuo000 on 2010-12-28
> **trent.josephsen said:**
> My Java is rusty, but I do believe that's caused by a faulty package line in the .java file.  "package main;" perhaps?  Delete it and everything should be fine.

Thank you. I could run the HelloWorld using command "java HelloWorld" once I deleted the line "package main;" in the source code.

But what if I actually want to put some java files into one package and have another java file import that package? Then how should I compile and run the program in this case?

---

### Post by jdonnell on 2010-12-28
you should use either ant or maven. Ultimately you have to learn how the java class path works.

[http://download.oracle.com/javase/1.5.0/docs/tooldocs/windows/classpath.html](http://download.oracle.com/javase/1.5.0/docs/tooldocs/windows/classpath.html)
[http://ant.apache.org/](http://ant.apache.org/)
[http://maven.apache.org/](http://maven.apache.org/)

---

### Post by trent.josephsen on 2010-12-28
The "package" line prepends "main." to the class name.  In order to call the class with the **java** binary, you must call it by its full name:
```
java main.HelloWorld
```
But **java** won't look in the current directory for that class (./HelloWorld.class); it looks for ./main/HelloWorld.class.

The simple and quick fix is to put all the .class files that belong in the *package* main into the *directory* main.

With the "package main" line in HelloWorld.java, this works:

```
$ mkdir main
$ mv HelloWorld.java main
$ javac main/HelloWorld.java
$ java main.HelloWorld
```

For all but the simplest programs, you should consider an automated make solution like ant.  This should get you started though!

---

### Post by spearfish on 2011-01-03
I had a similar problem with a new install of Java on a new laptop.  My classpath was not set right.

My fix was to go into the .bashrc file and make sure the . (dot) directory was in the classpath so that java could see the file I had just compiled in my current directory.

In my .bashrc file there are a few lines that look like this:

# added for Java
JAVA_HOME=/home/username/jdk1.6.0_23
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=$JAVA_HOME/lib:.

The little addition of the :. was what made the JDK tool "java" go to the current directory.  :)

Before, if I typed:
$ javac helloworld.java

and then 

$ java hello
it would say there was an error loading the class, because it didn't know where to look.  When you add . to the CLASSPATH it knows where to search for classes you just compiled.

---

### Post by davmaz on 2011-01-08
> **trent.josephsen said:**
> The "package" line prepends "main." to the class name.  In order to call the class with the **java** binary, you must call it by its full name:
```
java main.HelloWorld
```
But **java** won't look in the current directory for that class (./HelloWorld.class); it looks for ./main/HelloWorld.class.

The simple and quick fix is to put all the .class files that belong in the *package* main into the *directory* main.

With the "package main" line in HelloWorld.java, this works:

```
$ mkdir main
$ mv HelloWorld.java main
$ javac main/HelloWorld.java
$ java main.HelloWorld
```

For all but the simplest programs, you should consider an automated make solution like ant.  This should get you started though!

I thought I had finally seen a solution to what I thought was not having CLASSPATH set correctly here. But even this does not work on my machine. It still prints:
13:41 ~ > javac main/HelloWorld.java
13:49 ~ > java main.HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: main/HelloWorld (wrong name: HelloWorld)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClassCond(ClassLoader.java:632)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:616)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
13:49 ~ > 

This is driving me nuts!

---

### Post by trent.josephsen on 2011-01-09
That's because you deleted the "package main;" line.  When you moved it to a subdirectory, you caused the opposite of your original problem:  you can now find the file main/HelloWorld.class, but since it's internally labeled as just HelloWorld (not main.HelloWorld) java says "Wait, something's gone wrong here, this class's internal name doesn't match where I found it in the filesystem."

It makes a twisted amount of sense if you don't think about it too much.  (This is one of the reasons I don't like Java as a first language.)

Sorry for the late response, I've been incommunicado :/

---

