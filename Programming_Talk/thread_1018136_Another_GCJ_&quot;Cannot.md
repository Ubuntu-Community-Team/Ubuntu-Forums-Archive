---
title: "Another GCJ &quot;Cannot"
date: 2008-12-21
forum: Programming Talk
---

### Post by semprance on 2008-12-21
Well I've mucked up the title lets see if I can not muck up the rest of the post :-(

I get this when I try to compile:

```
jack@SEMPdesktop:/media/disk/Documents/Java/1 - Simple Programs/Speed Calculator$ gcj --main=SpeedCalc -o SpeedCalc SpeedCalc.java
SpeedCalc.java:1: error: The import java.util.Scanner cannot be resolved
	import java.util.Scanner;
	       ^^^^^^^^^^^^^^^^^
SpeedCalc.java:9: error: IOException cannot be resolved to a type
	public static void main (String [] args) throws IOException
	                                                ^^^^^^^^^^^
SpeedCalc.java:23: error: Scanner cannot be resolved to a type
	Scanner in = new Scanner(System.in);
	^^^^^^^
SpeedCalc.java:23: error: Scanner cannot be resolved to a type
	Scanner in = new Scanner(System.in);
	                 ^^^^^^^
4 problems (4 errors)

```

I'm not using netbeans and my 'java' and 'javac versions are sound. I'll post the update-alternatives list in a mo.

Anyone got an idea? (Also the IOException goes away when the correct import is included so it is JUST the Scanner that will not work.)

I'm using jre/jdk1.6.0

EDIT: New info ---

```

jack@SEMPdesktop:/media/disk/Documents/Java/1 - Simple Programs/Speed Calculator$ sudo update-alternatives --config javac

There are 2 alternatives which provide `javac'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/bin/javac
          2    /usr/bin/gcj-wrapper-4.3

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.

```

---

### Post by CptPicard on 2008-12-21
Why are you using gcj? That uses the GNU Java which doesn't include Scanner... use "javac" to compile.

---

### Post by semprance on 2008-12-21
That would explain my problem :-)

I want to create native executables for some of my java programs and read that GCJ could do it. Is there another native compiler that does include Scanner?

EDIT: Or is there a way of getting the GCJ compiler to use the standard JRE 1.6.0?

---

### Post by CptPicard on 2008-12-21
Not that I know of... why do you want to compile to native? It just makes distribution harder and my experience tends to tell me there is no substantial speedup.

---

### Post by semprance on 2008-12-22
I'm confused. What is the best way to distribute? As .class files?

Sorry as you can tell I'm fairly new to all this (Java as well as this forum).

---

### Post by SeanHodges on 2008-12-22
You want to use the JDK compiler, not the GCJ one:

```
javac SpeedCalc.java
```

then run it using:

```
java SpeedCalc
```

This talk of "native" is a bit misleading I think; you are compiling a SpeedCalc.class file, which the java program will run when you type the above command. The best way to distribute a small program like this is to provide the .java source file for others to compile, unless you wish to package it for non-technical users.

---

### Post by CptPicard on 2008-12-22
For sake of completeness, "the" way to distribute is as .class files packaged into a .jar file :)

---

### Post by semprance on 2008-12-22
Ah ok I get it :-)

I just wanted something that a novice user could pick up and use without having to understand how to compile and run using the JRE/JDK from command the command line.

I'll make them in to jar files instead as running them is fairly easy (I can just include a readme file with the programs).

Thanks for the help :-) And for politely ignoring my accidentally missing out half of the title of the thread...

---

### Post by bruce89 on 2008-12-22
> **semprance said:**
> I just wanted something that a novice user could pick up and use without having to understand how to compile and run using the JRE/JDK from command the command line.


They'd need to have Classpath and GCJ installed as well though.

---

### Post by semprance on 2008-12-22
I've been reading up on making debian packages today. Could I make the Classpath and GCJ (along with JRE/JDK) dependencies for a package of the program? Or is that not the right way to do it. I'm still unclear on some of the little details for making a deb package from java files. :S

---

### Post by CptPicard on 2008-12-22
> **semprance said:**
> Could I make the Classpath and GCJ (along with JRE/JDK) dependencies for a package of the program?

Why both? You only need one or the other depending on what you are distributing. But you really should forget about gcj (I have no idea where you got the idea from). The cleanest, minimal set of dependencies is just the JRE (you don't need the Development Kit with its compiler to just run stuff).

---

### Post by Reiger on 2008-12-22
If you're problem is with the compiling bit: that's the point with .class files -- these are already compiled but require the runtime to work.

GCJ compiled 'executables' still require a minimal runtime IIRC (the Classpath thing for instance). However a properly set up Jar file (include a MANIFEST file which contains a pointer to your 'main' entry point for the code contained within the JAR) is itself just as executable, only it requires the full runtime. Either way you're not going to get away without dependencies on some kind of Java runtime so you may as well stick with the best Java option you have. Which is first the one which implements the Java Language Specification most fully and second the one which offers best performance (or minimal RAM footprint depending on what you consider 'best' and 'performance'). ... Both rule out the GCJ: it's stuck at Java 1.4 and I'm not sure if it is actually a full implementation of Java 1.4... Sun is closer to Java 1.7 now. :D

---

### Post by semprance on 2008-12-23
Ah ok. Just a dependency on the JRE then. I guess I'll go with 1.6 seeing as it's the latest (and also what I use personally). 

Thanks for clearing this up for me everyone :-)

---

