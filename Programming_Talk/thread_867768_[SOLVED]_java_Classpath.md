---
title: "[SOLVED] java Classpath?"
date: 2008-07-23
forum: Programming Talk
---

### Post by ballard on 2008-07-23
Hallo guys!

I tried to run a small "hello world"-java program but it didnt work. ( I installed suns java-6-sdk)
compilation works without problems but runnin:
```

# java hellow.class 
Exception in thread "main" java.lang.NoClassDefFoundError: hellow/java
Caused by: java.lang.ClassNotFoundException: hellow.java
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

so already tried with the working directory in Classpath and with "/usr/lib/jvm/java-6-sun/jre/bin/" but nothing worked ...

what is the right way to get them running on Ubuntu ?

Edit: corrected the comand #java hellow.java -> #java hellow.class

---

### Post by Zugzwang on 2008-07-23
That's a repeating problem. Look [here]("http://ubuntuforums.org/showthread.php?t=692571&highlight=Java+package") for a solution (your problem is that your directory structure might not reflect the package structure and you are not running your program from your "root package directory"), it is mentioned in post #5.

EDIT: Ok, I didn't read the post well enough. Forget about that and read the next post.

---

### Post by henchman on 2008-07-23
hello!

you first have to compile the *.java files by invoking the java compiler javac

```
javac hellow.java
```

then you can execute the compiled class file which includes your main function by doing

```
java hellow
```

hf :>

---

### Post by ballard on 2008-07-23
hmmm no. i don't think so i dont use any packages.

Just the hellow.class
```

public class hellow {

public static void main(String[] args) {
System.out.println("Hello World!");
}

}

```

sorry i dont see the package problem :(


EDit: and I din'T post the right .... correct Code now:
```

# java hellow.class
Exception in thread "main" java.lang.NoClassDefFoundError: hellow/class
Caused by: java.lang.ClassNotFoundException: hellow.java
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

i do compile before *g*

---

### Post by Zugzwang on 2008-07-23
> **ballard said:**
> 
sorry i dont see the package problem :(

Right - there is none. I didn't read your post well enough. Just follow the advise by henchman. The trick is that you omit the ".java" extension when starting the program using the "java" command.

---

### Post by ballard on 2008-07-23
> **Zugzwang said:**
> Right - there is none. I didn't read your post well enough. Just follow the advise by henchman. The trick is that you omit the ".java" extension when starting the program using the "java" command.

Sorry this was wrong in the post,
I tried the right on the console ... with .class ;)

---

### Post by Tomosaur on 2008-07-23
^^Think you may have solved your problem (If you could mark the thread as solved, it'd help future readers :P ), but for future readers:

To compile and run a Java program:

```

javac hellow.java

```

```

java hellow

```

Notice that you do not add the '.class' part of the program name.

---

### Post by ballard on 2008-07-23
Oh! **No. isn't solved**. I just *posted* the false command.

I just repeat the hole...

I installed Java (sun-java6-sdk).
wrote file:
[QUOTE=hellow.java]
public class hellow {

public static void main(String[] args) {
System.out.println("Hello World!");
}

}
[/QUOTE]

than compile:
```
$ javac hellow.java
```
(successful)
and then tried to run:
```
$ java hellow.class
```
or
```
$ java hellow
```

both result in:
```
Exception in thread "main" java.lang.NoClassDefFoundError: hellow
Caused by: java.lang.ClassNotFoundException: hellow.java
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

---

### Post by tinny on 2008-07-24
What version of Ubuntu do you have?

Quick check, what is the output of...

```

java -version
javac -version

```

Can you see the "hellow.class" after you have run "javac hellow.java"?

Also you are running "java hellow" in the same dir as the hellow.class file is in right?

---

### Post by drubin on 2008-07-24
Java Classes are NOT allowed to have spaces " " in them.... I would very highly recommemd renaming your class to something with out spaces.

Ps Java Sourcefile names need to corrispond to the class inside of them.

```
HelloWorld.java 
public class HelloWorld{

}
```

---

### Post by drubin on 2008-07-24
Miss read the OP, please ignore my last comment :(

---

### Post by CameO73 on 2008-07-24
First make sure you have **sun-java6-jdk** and **sun-java6-jre** installed.

Then this should work:

[LIST]
[*]create a file HelloWorld.java with the following contents: ```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```
[*]execute **javac HelloWorld.java** in a console
[*](a HelloWorld.class file is now created if everything went succesfully)
[*]execute **java HelloWorld** in the same directory
[/LIST]
For me it prints 'Hello World!' to the console.
Let me know how it works for you (or the exact error message if anything went wrong).

---

### Post by CameO73 on 2008-07-24
For the record: the error message you see is (in this case) caused by a missing .class file. If you specify a file that doesn't exist, you get that exact message. In fact, that last error message you mention seems to indicate that you tried to execute **java hellow/java**. 

Make sure you type the exact .class name (without the .class part) and that the .class file does indeed exist!

On a related note: you really want to use an IDE (Integrated Development Environment) if you want to learn Java. A good one is [Eclipse](http://www.eclipse.org/).

---

### Post by ballard on 2008-07-24
Ubuntu: Hardy Heron (8.04)
```
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
$ javac -version
javac 1.6.0_06
```

> **tinny said:**
> 
Also you are running "java hellow" in the same dir as the hellow.class file is in right?
Yes, same dir.

```
$ apt-get install emerge sun-java6-jdk
...
sun-java6-jdk is already the newest version.

$ apt-get install sun-java6-jre
...
sun-java6-jre is already the newest version.
```

Ok so I tried exactly your example:
```

$ nano HelloWorld.java
$ javac HelloWorld.java
$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
Caused by: java.lang.ClassNotFoundException: HelloWorld
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

and the HalloWorld.class-file was really created:

```
Êþº¾^@^@^@2^@^]
^@^F^@^O        ^@^P^@^Q^H^@^R
^@^S^@^T^G^@^U^G^@^V^A^@^F<init>^A^@^C()V^A^@^DCode^A^@^OLineNumberTable^A^@^Dmain^A^@^V([Ljava/lang/String;)V^A^@
SourceFile^A^@^OHelloWorld.java^L^@^G^@^H^G^@^W^L^@^X^@^Y^A^@^LHello World!^G^@^Z^L^@^[^@^\^A^@
HelloWorld^A^@^Pjava/lang/Object^A^@^Pjava/lang/System^A^@^Cout^A^@^ULjava/io/PrintStream;^A^@^Sjava/io/PrintStream^A^@^Gprintln^A^@^U(Ljava/lang/String;)V^@$
^@^@^@^F^@^A^@^@^@^A^@  ^@^K^@^L^@^A^@  ^@^@^@%^@^B^@^A^@^@^@   ²^@^B^R^C¶^@^D±^@^@^@^A^@
^@^@^@
^@^B^@^@^@^C^@^H^@^D^@^A^@^M^@^@^@^B^@^N
```

---

### Post by Zugzwang on 2008-07-24
Ah, I see. Make sure that the name of the class is the same as the filename of the .java file. So if you call your class "hellow", you need to put it into "hellow.java" - And: the file name is case sensitive! 

If everything is OK with respect to this issue, please append the generated .class file to your next reply so that we can decompile it for checking whether the running or the compiling causes problems.

Also try "java -cp . HelloWorld" - Does that help? Just a gues...

---

### Post by ballard on 2008-07-24
> **Zugzwang said:**
> Ah, I see. Make sure that the name of the class is the same as the filename of the .java file. So if you call your class "hellow", you need to put it into "hellow.java" - And: the file name is case sensitive! 

I am sure.



> **Zugzwang said:**
> 
Also try "java -cp . HelloWorld" - Does that help? Just a gues...

Damn, YES! this works ... but why   i allready added the current directory to the CLASSPATH  what is the diference ?

---

### Post by CameO73 on 2008-07-25
I'm still curious. Normally when the CLASSPATH is not set, Java will use the classes in the current directory and its built-in classes. If you set the CLASSPATH to anything, it won't automatically include the current directory, unless you added it yourself.

So I'm now guessing you have set the CLASSPATH, but for some reason don't have the current directory in it. This can happen if you make a mistake in the CLASSPATH (e.g. when you forget or mistype the path separators).

Could you paste your CLASSPATH variable here (e.g. type in the console **echo $CLASSPATH** and copy the result).

---

### Post by ballard on 2008-07-25
Damn your right.

My first Mistake was that i tried to run the Prog with *java HelloWorld.class*
And than tried to work with the Classpath  ... and make there the mistake.

Thank you everyone helped my :KS

---

### Post by vipbk09 on 2009-09-16
> **ballard said:**
> Damn your right.

My first Mistake was that i tried to run the Prog with *java HelloWorld.class*
And than tried to work with the Classpath  ... and make there the mistake.

Thank you everyone helped my :KS

Me too :(

```
$ java Hellow
Exception in thread "main" java.lang.NoClassDefFoundError: Hellow/class
Caused by: java.lang.ClassNotFoundException: Hellow
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: Hellow.  Program will exit.
``````
$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun

``````
$ echo $CLASSPATH
/usr/lib/jvm/java-6-sun/bin

```I don't no. Please help me.

Thanks.

---

