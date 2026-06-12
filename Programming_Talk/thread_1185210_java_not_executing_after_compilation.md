---
title: "java not executing after compilation?"
date: 2009-06-12
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-12
what is basic error in this? i did this in vim and saved as j1.java

```

class myapp {
 public static void main(String args[]) {
  System.out.println("i code java");
 }
}


```
```

abhilash@abhilash:~$ javac j1.java
abhilash@abhilash:~$ java j1
Exception in thread "main" java.lang.NoClassDefFoundError: j1
Caused by: java.lang.ClassNotFoundException: j1
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

why is not executing,

---

### Post by Linteg on 2009-06-12
Because the file doesnt exist, javac creates classname.class files, try running java myapp

---

### Post by jespdj on 2009-06-12
First of all, you have to make your class myapp **public**:
```
public class myapp {
  // ...
```
Second, Java requires that source file names are named after the public class they contain. So your file must be named myapp.java, not j1.java. Rename your source file and then compile and run it like this:
```
javac myapp.java
java myapp
```

See Sun's [Hello World tutorial](http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html).

---

### Post by rocketflame on 2009-06-12
class names need to start with a **CAPITAL**

myapp should be 

Myapp

you should also save the file with the class name, so the file name should be

Myapp.java

---

### Post by Zugzwang on 2009-06-12
> **rocketflame said:**
> class names need to start with a **CAPITAL**


This is just a part of the Java code conventions, but not a strict requirement. The equivalence of the class name and the .java file name is however a requirement.

---

