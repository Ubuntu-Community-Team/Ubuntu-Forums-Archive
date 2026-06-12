---
title: "Starting java"
date: 2011-11-27
forum: Programming Talk
---

### Post by Befind on 2011-11-27
Ok, I don't want to be that guy but I couldn't find the info I needed after searching the forums for 1/3 an hour.
I want to learn JAVA but I have no idea where to get the tools I need to start or what they are exactly. The extent of my programming experience is Q-Basic, I made quite a few rougelike games back than and the itch resurfaced recently when I rediscovered RL the other day. I know that JAVA has been used in making portable games and applications, i know it can be done with other languages too but Java seems to stand out for me.

I just want to know where I can get the compilers, language and all the other tools I need to get started

Thanks in advanced!!!!

---

### Post by ask_ on 2011-11-27
First you need to have Java run-time environment on your system.
You could install the open-jdk runtime environment via Synaptic package installer on your ubuntu system.

Then you will also need a compiler , you could try gcj compiler, this is also available from the Synaptic package installer.


There are other run-time environments and other compilers for Java too. Sun also provides it's own runtime and compilers.

Finally, a great place to start learning Java, in case you haven't seen this before :-

[http://docs.oracle.com/javase/tutorial/](http://docs.oracle.com/javase/tutorial/)

Creating your first Hello World program in Java for Linux systems via command-line, just to get you started - 
[http://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html#unix-2a](http://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html#unix-2a)   :D


For further info read the community documentation page for Java on Ubuntu -
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
Here you will find info on the different runtime environments - OpenJDK , Sun Java and so on. Install whichever suits you.

---

### Post by Befind on 2011-11-27
Thank you, the java runtime program allows me to use the language as well?

---

### Post by ask_ on 2011-11-27
If by using the language, you mean creating your own executable programs from source code,then ,no.

To compile your code into executable file, you need to have a Java compiler installed on your system.

The runtime can be used even if your needs are not in programming. For instance to run java applications available on internet you need the runtime. But, it won't help you to compile the programs you create.

Install GNU Java Compiler(gjc) for that or any other which you like.

(in the HelloWorld app example, you will see that source code is written in .java file. To convert into executable file i.e .class file, you need to use the following command on terminal:-
```
javac HelloWorldApp.java

```
in absence of gjc compiler or any other similar one, you won't be able to run this command.

After you succesfully compile, you get .class file which is executable, to run this file, you need to use following command :-
```
java HelloWorldApp

```
This command can be executed only if you have runtime installed.
)

Cheers!

---

### Post by ofnuts on 2011-11-27
> **Befind said:**
> Ok, I don't want to be that guy but I couldn't find the info I needed after searching the forums for 1/3 an hour.
I want to learn JAVA but I have no idea where to get the tools I need to start or what they are exactly. The extent of my programming experience is Q-Basic, I made quite a few rougelike games back than and the itch resurfaced recently when I rediscovered RL the other day. I know that JAVA has been used in making portable games and applications, i know it can be done with other languages too but Java seems to stand out for me.

I just want to know where I can get the compilers, language and all the other tools I need to get started

Thanks in advanced!!!!In your Ubuntu repository you can pick either open-jdk or sun-java-jdk. 
These normally drag in the java runtime, and contain the basic utilities, including the "javac" compiler.

If you want an IDE, the two main IDEs used with Java are Eclipse and Netbeans. AFAIK Netbeans is better for graphics, and Eclipse is more on the "java for servers" (aka J2EE) side of things and less handy to develop Swing applicaltions (IBM sells IDEs build around Eclipse for java server development). Both are also available in the Ubuntu repositories.

---

### Post by jespdj on 2011-11-27
> **ask_ said:**
> Install GNU Java Compiler(gjc) for that or any other which you like.
No, don't get gcj. It is far behind the current version of the Java programming language and it's not the "official" Java compiler. Nobody uses gcj for any serious project.

If you want the latest version of Java and you want to have the compiler so that you can compile your own Java programs, then download the JDK (not the JRE) from Oracle: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

Download either the Linux i586 package (32-bit) or the Linux x64 (64-bit) package (depending on if you're running 32-bit or 64-bit Ubuntu). Get the .tar.gz version (not the .rpm version). Unpack it with:
```
tar xfz jdk-7u1-linux.tar.gz
```
and then add the "bin" directory to your PATH. Read the [README](http://www.oracle.com/technetwork/java/javase/jdk-7-readme-429198.html).

Oracle's [Java Tutorials](http://docs.oracle.com/javase/tutorial/) are the best place to start learning how to use the JDK and learn programming in Java.

---

