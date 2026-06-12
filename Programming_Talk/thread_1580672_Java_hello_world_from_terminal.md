---
title: "Java hello world from terminal"
date: 2010-09-23
forum: Programming Talk
---

### Post by worldsayshi on 2010-09-23
Developing, compiling and running in Eclipse works without problems. But as I try to run in a terminal I face trouble:

Trying on a hello world example:
```
package test;

public class Main {
	public static void main(String[] args){
		System.out.println("Hello");
	}
}

```
I run javac Main.java in the test folder. Works fine. But when running "java Main.class" (or similar for "java Main") I get the following error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: Main/class
Caused by: java.lang.ClassNotFoundException: Main.class
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: Main.class. Program will exit.

```


Any ideas? :S 
Can it be a problem with the openJDK (64 bit)?
java -version gives me:
```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)

```

I don't have a lot of experience running java from terminal. So I might do something wrong.

---

### Post by GregBrannon on 2010-09-23
Try:

```
> java Main
```

---

### Post by spjackson on 2010-09-23
```

$ cd ..
$ ls test
Main.class  Main.java
$ java test.Main

```

---

### Post by worldsayshi on 2010-09-23
Thanks! java test.Main worked!

Testing my other project seems to work as well, even with multiple classes and modules!

But I wonder also if there is a way to control the working directory? So that from terminal I can make the program "believe it is in another directory, like the project root and not the bin folder where it lies.

---

### Post by brydonhunter on 2010-09-23
> **spjackson said:**
> ```

$ cd ..
$ ls test
Main.class  Main.java
$ java test.Main

```

+1, learned something new !

---

### Post by KdotJ on 2010-09-23
The reason why 

```
java Main
```

didn't work is because you have it in a package. If you removed the 

```
package test;
```

from the code than it would work by just running Main from the working directory. Of course the method that spjackson works fine, but that's just some info for you

---

