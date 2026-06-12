---
title: "Running my HelloWorld java"
date: 2007-03-03
forum: Programming Talk
---

### Post by Baelfael on 2007-03-03
When I try to run my Java HelloWorld program, I get the message:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Hello (Unsupported major.minor version 50.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

---

### Post by Baelfael on 2007-03-03
Here's my code:

```
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World!"); 
    } 
}

```

---

### Post by laxmanb on 2007-03-03
I think you've installed the JDK but haven't registered it's JRE with your system....

try running **java -version** any note the output... i'm almost sure it will be GNU Classpath... in that case, there are instructions for registering the JRE on this forum, just search for them...

---

### Post by Baelfael on 2007-03-03
It returned with this:

```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

---

### Post by laxmanb on 2007-03-03
So, which version of the JDK do you have, run, **javac -version**

---

### Post by Baelfael on 2007-03-03
It said 1.6.0.

---

### Post by laxmanb on 2007-03-04
See, javac is compiling for Java 1.6, but your JRE is still 1.4.2. 

here, follow this guide and skip some of the steps like extracting the JDK from the bin file, etc...:

[http://trac.centricware.org/wiki/2007/01/28/21.58](http://trac.centricware.org/wiki/2007/01/28/21.58)

---

### Post by Baelfael on 2007-03-04
That guide is really confusing me. It doesn't seem straight forward enough. Keep in mind I am pretty new to Linux and Java programming.

---

### Post by phossal on 2007-03-04
Install Java's JDK in six steps. You can use the guide in my signature. Or, as an alternative, you can enable the backports repository and use:
```
sudo apt-get install sun-java6-jdk
```




> **laxmanb said:**
> here, follow this guide and skip some of the steps like extracting the JDK from the bin file, etc...: Who wrote that guide? It's *awful*. The funniest part is the question about 32 or 64 bit, where he says he doesn't understand the reason for using 32bit on a 64bit arch, and then includes a link that is a bug *with 64bit Java*. That's funny. Pretty clear the author doesn't *get it.* One reason a person (like me) might use 32bit Java is because *SUN* recommends it in certain cases - like for applet support. The second reason is that manually installing 32 bit Java and 32 bit eclipse is a combination that makes *eclipse* perform as well as on Windows. Many, many people have complained about how poorly eclipse performed using various JDK's (and methods of installing them). That very issue is what prompted me to look for a new way of aquiring my software - I was eclipse dependent and used to the speed of Windows - and I ended up trying every available combination of eclipse and Java on my AMD 64. The answer? 32/32. ;) Things change, and hopefully improve. It may not *always* be true that it's *better* to use the 32bit packages - but it definitely *was* as 6.0 was rolling out.

---

### Post by Baelfael on 2007-03-04
```
 Who wrote that guide? It's *awful*.
```
So it's not just me. :D

Am currently trying your guide, phossal. I'll report back.

---

### Post by Baelfael on 2007-03-04
...It didn't work. :( I still get the same message when I try to run a class file.

EDIT: I'm not going to waste my time. I'm just going to use an old Win98 box for Java development.

---

### Post by phossal on 2007-03-04
Nah, don't give up. How are you *compiling* that, and what command are you using to launch it? Can you put them, and the output if any?

Also, post the output to these two:
```
java -version
javac -version
```

What architecture are you using? Not a 64bit? And you're not running Beryl, right?

---

### Post by Baelfael on 2007-03-04
Well I compile it using 
```
javac Hello.java
```

java version:
```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
```
javac:
```
javac 1.6.0
```

---

### Post by phossal on 2007-03-04
> java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)


No Good. You're compiling using Java 1.6 (6.0), but trying to *run* your program using 1.4. Run:
```
sudo update-alternatives --config java
```
And choose the right one. Your program is compiled using JDK 6.0, but you're trying to run it using 1.4.

---

### Post by Baelfael on 2007-03-04
THANK YOU! That worked! :D

---

### Post by harakiri1976 on 2007-11-27
Hi Guys!


I was having the same problem.

1st: Created a HelloWordApp.java file using a text editor


```
/**
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */
class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}
```

2nd: Saved the file as HelloWorldApp.java

3rd: Compiled the HelloWorldApp.java:

```
nuno@nuno-desktop:~/Java$ javac HelloWorldApp.java
```

After compiling there's another file created - HelloWorldApp.class
```

nuno@nuno-desktop:~/Java$ ls
HelloWorldApp.class  HelloWorldApp.java


```
Now, the problem...

4th: Running the HelloWorldApp.java:
```

nuno@nuno-desktop:~/Java$ java HelloWorldApp 
Exception in thread "main" java.lang.ClassFormatError: HelloWorldApp (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)


```

So, I've checked my java and javac versions.

```

nuno@nuno-desktop:~/Java$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
nuno@nuno-desktop:~/Java$ javac -version
javac 1.6.0


```

Then, I ran..  [COLOR="Blue"]sudo update-alternatives --config java[/COLOR]
```

nuno@nuno-desktop:~/Java$ sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/bin/java-sablevm

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.


```

..and chose java-6-sun for my JRE.

After that, I made it :)

```

nuno@nuno-desktop:~/Java$ java HelloWorldApp 
Hello World!


```

Thank You! I followed your Help topics. Just wanted to post all steps to help maybe somebody else.

---

