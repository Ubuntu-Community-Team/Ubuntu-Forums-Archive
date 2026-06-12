---
title: "Simple Java program"
date: 2009-04-21
forum: Programming Talk
---

### Post by lil_kid1333 on 2009-04-21
Well I'm having trouble writing this simple Java program

```
import java.util.*;

public class InputOutput {
	
	public static void main(String[] args) {
		int number1;
		int number2;
		Scanner input = new Scanner(System.in);
		
		System.out.print("Please input your 1st number: ");
		number1 = input.nextInt();
		
		System.out.print("Please input your 2nd number: ");
		number2 = input.nextInt();
		
	}
}
```

Here are the instructions the teacher gave us...

"Write a Java program that asks the user to enter two integers, obtains them from the user, and prints the sum, difference, product, and quotient for these two integers. Use the techniques as presented in class and used in the last assignment."

I wrote down some notes and thats exactly what he used what i'm using but it doesn't work with me. Well I haven't finished the rest of it, 1st I wanted to compile to make sure it would work so far but I get 2 errors saying "Scanner cannot be resolved to a type." at Line 7

What am I doing wrong? :'(

---

### Post by DrFugly on 2009-04-21
Scanner is a relatively new class, introduced in Java 5.0 Make sure that you're using at least that. To check your java version run: 'java --version'

Good luck!

---

### Post by shadylookin on 2009-04-21
you're using the gcj version of java which is horrendous and for whatever reason they won't stop making it the default. go into synapic search for java and download sun-java6-sdk

then make sure you're using it
sudo update-alternatives --config java

then select sun java

If you're using an IDE like eclipse make sure you change the compiler version to this new version of java

to do this in eclise click on window in the taskbard then preferences. when the popup comes up click on java then installed jres. Now click add. then browse. the jre should be in /usr/lib/jvm/java-6-sun. Then click ok and everything should be fine

---

### Post by lil_kid1333 on 2009-04-21
Well this is what I get from the java --version command

:~$ java --version
Unrecognized option: --version
Could not create the Java virtual machine.

And ok I'll try downloading the sdk which I'm pretty sure I downloaded... :S

This is what I have on the window on Eclipse...

[IMG]http://img183.imageshack.us/img183/8970/java.png[/IMG]

---

### Post by lil_kid1333 on 2009-04-21
This is what I get from the sudo update-alternatives --config

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/gij-4.2
          4    /usr/bin/gij-4.3
          5    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 


What I do??

---

### Post by shadylookin on 2009-04-21
/usr/lib/jvm/java-6-sun/jre/bin/java

I would go with that one

---

### Post by Reiger on 2009-04-21
I'd go with (1) at the moment. However your problem is that Eclipse tries to build your application for/using the GCJ - not the SUN/OpenJDK versions! GCJ isn't Java 1.5, it is 1.4 with some 1.5 support (most notably: no good Swing and Util support).

---

### Post by lil_kid1333 on 2009-04-21
> **Reiger said:**
> I'd go with (1) at the moment. However your problem is that Eclipse tries to build your application for/using the GCJ - not the SUN/OpenJDK versions! GCJ isn't Java 1.5, it is 1.4 with some 1.5 support (most notably: no good Swing and Util support).

Well I switched to number 1 but how to I fix it so it uses the jdk?

My program still doesn't compile... :'(

---

### Post by bettlebrox on 2009-04-21
> **lil_kid1333 said:**
> Well I switched to number 1 but how to I fix it so it uses the jdk?

My program still doesn't compile... :'(

On your screenshot there's an "Add" button on the top right. Use that to add the 1.6 JVM and then make it the default for your workspace and recompile.

---

### Post by lil_kid1333 on 2009-04-22
> **bettlebrox said:**
> On your screenshot there's an "Add" button on the top right. Use that to add the 1.6 JVM and then make it the default for your workspace and recompile.

I'm sorry but how would I do that? I looked up the directory and I get this:

[IMG]http://img515.imageshack.us/img515/7339/java1.png[/IMG]

:S

---

### Post by lil_kid1333 on 2009-04-22
wait never mind I Think I got it. All I get are 2 warnings but other then that it compiled ^^ thanks dudes :)

is their a way to run it from the terminal?

---

### Post by shadylookin on 2009-04-22
to compile it from the terminal use 

javac YOURFILENAME.java

then it will create a class file which you can run with

java YOURFILENAME

do not include .class at the end

---

### Post by lil_kid1333 on 2009-04-22
Yeah I tried that but I get the following:

:~$ java InputOutput
Exception in thread "main" java.lang.NoClassDefFoundError: InputOutput
Caused by: java.lang.ClassNotFoundException: InputOutput
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: InputOutput.  Program will exit.

---

### Post by Zugzwang on 2009-04-22
> **lil_kid1333 said:**
> Yeah I tried that but I get the following:

:~$ java InputOutput
Exception in thread "main" java.lang.NoClassDefFoundError: InputOutput
Caused by: java.lang.ClassNotFoundException: InputOutput
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: InputOutput.  Program will exit.

...which means that you did not compile beforehand (into the current directory).

---

### Post by lil_kid1333 on 2009-04-22
nope it's right their both the .java and .class file

Well I used the cd command to change the path to where it's found but is their any other way to do it quicker? I don't like the eclipse thing that much >_>

I guess i'll suck it up and just get used to it...

---

### Post by Zugzwang on 2009-04-22
> **lil_kid1333 said:**
> nope it's right their both the .java and .class file

Well I used the cd command to change the path to where it's found but is their any other way to do it quicker? I don't like the eclipse thing that much >_>

I guess i'll suck it up and just get used to it...

Note that you always have to start and compile the program from its "package root", so for example if you have a class "foo" in a package "bar" then you create a directory called "bar", put "foo.java" in there and run:
```

javac bar/foo.java
java bar/foo

```
Always compile from the same directory as you run the program from. Otherwise you have to deal with classpaths.

---

### Post by HotCupOfJava on 2009-04-22
I'm not as familiar with Eclipse, but Netbeans will do automatic packaging, too. Which means you will have to add a classpath to your "java" command to run the app (assuming you allowed the IDE to compile it for you).

```
java -classpath "packageDirectory/nextDirectory:." MyApplicationClassName
```

---

