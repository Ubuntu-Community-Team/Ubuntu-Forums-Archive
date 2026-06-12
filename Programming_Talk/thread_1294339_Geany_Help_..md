---
title: "Geany Help ."
date: 2009-10-18
forum: Programming Talk
---

### Post by rsiddharth on 2009-10-18
I am trying to write my first program ( Java ) in the Geany IDE ( before I was using Netbeans IDE ) , I am able to write and compile the program successfully but when it I try to run ( Execute ) the program , the IDE is giving me errors . 

I tried figure this one out by myself by writing a simple program and I found that , the error has something to do with ' packages ' ( I am writing Java code ) . 

Here is my inference : 

*Whether I give the 'package' name or not the code is getting successfully compiled ,
*When I mention  'package' name in the code , compilation is successful but Execution gives out errors . 
*When I don't mention the 'package' name in the code , both compilation and the Execution are successful . 

Here is the simple code that I tried to run in geany :

```

package strings; // package name mentioned . Execution gives error .
/**
 * @author siddharth.
 *
 */

public class SGP {
public static void main(String[] args) {
    System.out.println("My First Program in Geany IDE! . ");
}
}


```The Error : 
```

Exception in thread "main" java.lang.NoClassDefFoundError: SGP (wrong name: strings/SGP)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: SGP. Program will exit.

```Can any one here point out where I am going wrong . 

Thank you for your help !

---

### Post by timvoet on 2009-10-18
i've never used Geany for java development, but the message is relatively precise.  You are trying to run a class packaged as SGP, where as you compiled it as strings.SGP.

check the run configuration, it should be trying to run strings.SGP not just SGP.

this is why it compiles and runs when you don't mention a package name.

---

### Post by OpenGuard on 2009-10-18
> **rsiddharth said:**
> 
*When I don't mention the 'package' name in the code , both compilation and the Execution are successful . 


Then why would you keep it ( haven't got so far yet ) ?

---

### Post by rsiddharth on 2009-10-19
> **timvoet said:**
> i've never used Geany for java development, but the message is relatively precise.  You are trying to run a class packaged as SGP, where as you compiled it as strings.SGP.

check the run configuration, it should be trying to run strings.SGP not just SGP.

this is why it compiles and runs when you don't mention a package name.
I don't really decipher what your trying to convey . It would nice you if explain it with a bit of eloboration . 

Thanks for your help .

---

### Post by konqueror7 on 2009-10-19
you declared your class 'SGP' in to be in the package 'strings', but apparently, your running 'SGP' outside of the 'strings' package. i haven't got to use geany but, try putting 'SGP' inside a folder named 'strings', or as OpenGuard said, declare 'SGP' with no package, as it would run normally...

---

### Post by rsiddharth on 2009-10-19
> **konqueror7 said:**
> you declared your class 'SGP' in to be in the package 'strings', but apparently, your running 'SGP' outside of the 'strings' package. i haven't got to use geany but, try putting 'SGP' inside a folder named 'strings', or as OpenGuard said, declare 'SGP' with no package, as it would run normally...
Thanks for your reply konqueror7 . I am very sure that I have placed SGP.java inside 'strings' directory .

---

