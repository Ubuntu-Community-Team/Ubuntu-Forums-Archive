---
title: "compiling a java program"
date: 2012-06-28
forum: Programming Talk
---

### Post by chaitanya525 on 2012-06-28
hello friends,
i am new to ubuntu. I want to compile my java program in ubuntu.so i installed open jdk 1.7 in ubuntu through sudo apt-get install command.
My java program is 
class Hai
{
 public static void main(String s[])
 {
   System.out.println("hai");
 }
}
But when i am compiling with javac there is no problem.
But with java command i am getting this error:
[U][B]Exception in thread "main" java.lang.UnsupportedClassVersionError: Hai : Unsupported major.minor version 51.0
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
Could not find the main class: Hai. Program will exit.[/B][/U]
This code was run successfully in windows. But in ubuntu with openjdk i am getting this error. Please help me......................

---

### Post by The Cog on 2012-06-28
That looks as though you might have two different java installations there. Can you post the output of these two commands?
```
java -version
javac -version
```

---

