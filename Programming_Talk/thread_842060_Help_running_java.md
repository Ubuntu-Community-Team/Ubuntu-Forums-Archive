---
title: "Help running java"
date: 2008-06-27
forum: Programming Talk
---

### Post by cheechandchong on 2008-06-27
Hi, I'm trying to run a simple Java program in the terminal:

```

class Hello {
    public static void main(String args[]){
      System.out.println("Hello, World!");
    }
}

```

I get the following error:

me@my-comp:~/Java$ java Hello.java
Exception in thread "main" java.lang.NoClassDefFoundError: Hello/java
Caused by: java.lang.ClassNotFoundException: Hello.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

I'm currently running:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

Any help on compiling and running this program would be appreciated!

---

### Post by LaRoza on 2008-06-27
[http://ubuntuforums.org/showthread.php?t=842038](http://ubuntuforums.org/showthread.php?t=842038)

Also, the sticky has a link to a thread on how to compile and run Java programs from start to finish. [http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622)

---

### Post by NovaAesa on 2008-06-27
or in other words, use the following commands:

```

javac Hello.java
java Hello
```

---

### Post by henchman on 2008-06-27
*javac* is the java compiler, which translates your java sourcecode into [bytecode]("http://en.wikipedia.org/wiki/Java_bytecode").

the *java* command opens a new [java virtual machine]("http://en.wikipedia.org/wiki/Java_Runtime_Environment") to execute this bytecode.

remember not to append .class when invoking *java*

---

### Post by Timdejager on 2008-06-27
> **cheechandchong said:**
> Hi, I'm trying to run a simple Java program in the terminal:

```

class Hello {
    public static void main(String args[]){
      System.out.println("Hello, World!");
    }
}

```

I get the following error:

me@my-comp:~/Java$ java Hello.java
Exception in thread "main" java.lang.NoClassDefFoundError: Hello/java
Caused by: java.lang.ClassNotFoundException: Hello.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

I'm currently running:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

Any help on compiling and running this program would be appreciated!

Also it should be String[] args

---

### Post by _sphinx_ on 2008-06-27
> **Timdejager said:**
> Also it should be String[] args

I think it should not matter.

---

### Post by henchman on 2008-06-27
> **_sphinx_ said:**
> I think it should not matter.

+1 

placement doesn't matter... you just have to pay attention when declaring multiple variables:

```
int[]   prims, matrix[], threeDimMatrix[][];
```

is the same as 

```
int prims[], matrix[][], threeDimMatrix[][][];
```

---

