---
title: "JAVA Background Process / Thread"
date: 2012-03-29
forum: Programming Talk
---

### Post by zobayer1 on 2012-03-29
Hello everyone, I need some help with writing java background programs. I am not quite used to Java (mainly C/C++ programmer) and I occasionally use it (rarely for school assignments).

I am writing a program which is basically some sort of server - client application. The server waits and keeps listening for any incoming client. Now, when I run the program, as expected, a window (console program) appears and then it executes nicely.

Is it possible to write a java program, when executed, won't show the window and not even in taskbar, but can be found in tasklists? I mean, the title of this post may be a bit misleading, as listening is already done in background, what I exactly want is to vanish the screen. I have searched for it in net, but all went over my head.

Also, in windows, when I create a jar file, I can run it with the command 
```
java -jar xyz.jar
```
But double clicking not working, while on many places I have seen it is written that double clicking should start the program nicely. I have jdk and jre installed properly. Still can't do it. Any help regarding this is highly welcome.

Thanks in advance. :KS

---

### Post by ofnuts on 2012-03-30
> **zobayer1 said:**
> Hello everyone, I need some help with writing java background programs. I am not quite used to Java (mainly C/C++ programmer) and I occasionally use it (rarely for school assignments).

I am writing a program which is basically some sort of server - client application. The server waits and keeps listening for any incoming client. Now, when I run the program, as expected, a window (console program) appears and then it executes nicely.

Is it possible to write a java program, when executed, won't show the window and not even in taskbar, but can be found in tasklists? I mean, the title of this post may be a bit misleading, as listening is already done in background, what I exactly want is to vanish the screen. I have searched for it in net, but all went over my head.

Also, in windows, when I create a jar file, I can run it with the command 
```
java -jar xyz.jar
```But double clicking not working, while on many places I have seen it is written that double clicking should start the program nicely. I have jdk and jre installed properly. Still can't do it. Any help regarding this is highly welcome.

Thanks in advance. :KS
1) the general answer is yes... awfully easy in Linux, but it seems you are in Windows, so please state your target operating system...

2) it all depends what is defined to open the JAR filetype in your file explorer. But in Windows it's a better idea to define a shortcut.

---

### Post by zobayer1 on 2012-04-17
> **ofnuts said:**
> 1) the general answer is yes... awfully easy in Linux, but it seems you are in Windows, so please state your target operating system...

2) it all depends what is defined to open the JAR filetype in your file explorer. But in Windows it's a better idea to define a shortcut.

Yes, I was in windows, linux is always better, but I was trying to do that on a friend's pc where linux was not available.

For the second part, I already used shortcuts (batch file), just thought it could be simple like clicking on the jar file and running it as I have seen many programs can be started in that way.

---

### Post by PaulM1985 on 2012-04-17
If you right click on the JAR file in Windows Explorer and go to Properties, there should be an "Opens With" section.  You can change this so that the program to open the JAR file is java.exe

Paul

---

### Post by zobayer1 on 2012-04-17
> **PaulM1985 said:**
> If you right click on the JAR file in Windows Explorer and go to Properties, there should be an "Opens With" section.  You can change this so that the program to open the JAR file is java.exe

Paul

Tried that, did not work, also I am having strange problem running java program from command promt, javac works just fine, and when I try java to run it, it says "Error: cannot find main class ... ". I am not using any package and as far as I remember this used to work just fine. Can it be a problem with java installation? should I try to re-install java?

---

### Post by PaulM1985 on 2012-04-17
Can you paste the output from:
```

java -version

```
```

javac -version

```

Does it definitely work when you do:
```

java -jar xyz.jar

```

You mentioned in your original post that this works ok.  Does it not now?

Paul

---

### Post by dwhitney67 on 2012-04-17
> **zobayer1 said:**
> Tried that, did not work, also I am having strange problem running java program from command promt, javac works just fine, and when I try java to run it, it says "Error: cannot find main class ... ". I am not using any package and as far as I remember this used to work just fine. Can it be a problem with java installation? should I try to re-install java?

I have the same trouble all the time; that's why I prefer Linux.

But, to answer your question, here's some steps that I performed to compile and run a simple program on Windoze:

Create Example.java:
```

public class Example
{
    public static void main(String[] args)
    {
        System.out.println("This is a simple program.");
    }
}

```
Compile Java code:
```

"%JAVA_HOME%\bin\javac" Example.java

```
Use your favorite editor to create the manifest file (manifest.mf) with these contents:
```

Main-Class: Example

```
Build the JAR file
```

"%JAVA_HOME%\bin\jar" cfm Example.jar manifest.mf Example.class

```
Execute the JAR file:
```

"%JAVA_HOME%\bin\java" -cp Example.jar Example

```
I hope this helps.

P.S.  You should ensure that JAVA_HOME is defined in your environment.  The commands above are quoted to guard against the possibility that JAVA_HOME is defined to be in a folder that contains a white-space in the name (e.g. Program Files).

---

### Post by zobayer1 on 2012-04-17
> **PaulM1985 said:**
> Can you paste the output from:
```

java -version

```
```

javac -version

```

Does it definitely work when you do:
```

java -jar xyz.jar

```

You mentioned in your original post that this works ok.  Does it not now?

Paul

This is the output I get from -version
```

C:\Users\You>java -version
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b17, mixed mode)

C:\Users\You>javac -version
javac 1.7.0

C:\Users\You>F:

F:\>cd JavaTest

F:\JavaTest>java -jar Main.jar
Hello World

F:\JavaTest>

```

So for an existing jar file it is working fine so far.

---

### Post by 11jmb on 2012-04-18
When you are double clicking to execute the jar file with java.exe, it may be trying to run

```
java xyz.jar
```

instead of 

```
java -jar xyz.jar
```

A quick search on stackoverflow turned this up, give it a try

[http://windowstipoftheday.blogspot.com/2005/10/setting-jar-file-association.html](http://windowstipoftheday.blogspot.com/2005/10/setting-jar-file-association.html)

---

