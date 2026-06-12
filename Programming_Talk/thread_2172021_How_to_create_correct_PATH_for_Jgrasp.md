---
title: "How to create correct PATH for Jgrasp"
date: 2013-09-02
forum: Programming Talk
---

### Post by kepa2 on 2013-09-02
Hi all!
I've had Ubuntu for a little while and i'm taking a computer science class programming in java. I don't know why my professor wants to use Jgrasp instead of Eclipse but whatever. I need help creating the correct path for Jgrasp. I finally got Jgrasp on Ubuntu but when I try to compile my program I get the error code

-jGRASP exec: javac -g Hello.java
 ----jGRASP wedge: could not execute  javac
 ----   error number 2.
 ----   
 ----   Target does not exist or is not on PATH.
 ----   u
 ----   
 ----   PATH is "/usr/lib/jvm/java-7-openjdk-i386/bin:/usr/lib/jvm/java-7openjdk-i386/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-7-openjdk-i386/bin".

 ----jGRASP: operation complete.

I've been looking at the following forums to help create the PATH so I can compile my work.

[http://ubuntuforums.org/showthread.php?t=44564](http://ubuntuforums.org/showthread.php?t=44564)
[http://ubuntuforums.org/archive/index.php/t-600798.html](http://ubuntuforums.org/archive/index.php/t-600798.html)

I just can't seem to set the correct PATH. I have OpenJDK Java 7 runtime installed (Because I read someplace that you need JDK to run Jgrasp). I also installed wine to run Jgrasp.

The code that I'm trying to compile in Jgrasp is the basic helloWorld.

public class Hello 
{
   public static void main(String[] args) 
   {
      System.out.println("Hello world!"); 
   }
}

Any help is deeply appreciated!

---

### Post by cariboo on 2013-09-03
This isn't a beginner question, moved to Programming Talk.

---

### Post by spjackson on 2013-09-04
I've never heard of jGRASP before, but it is a Java application: this should not be difficult. If it's hard, then you are doing it wrong.

I went to [http://www.jgrasp.org/](http://www.jgrasp.org/) clicked on Download, clicked on jGRASP.zip, then in a terminal ran
```

cd ~
unzip Downloads/jgrasp200_03.zip
jgrasp/bin/jgrasp

```
Hey presto! It works, compiles and runs Hello.

I have these packages installed openjdk-7-jre, openjdk-7-jdk.
```

$ echo $PATH
/home/spj/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

```
You don't need wine and you don't want to be trying to run jgrasp.exe under wine: that unnecessarily complicates matters.

How did you install the JDK? Was it via one of the Ubuntu package managers? Can you successfully run javac from the command line?

---

### Post by lbarowski on 2013-09-07
As you say, you have the "OpenJDK Java 7 runtime", which I assume doesn't include the compiler. You need the full JDK, or whatever OpenJDK calls it (seems confusing to have JDK in the name OpenJDK if they supply a runtime, which is by definition not a development kit).

---

### Post by gadwin2 on 2013-09-27
Guys Im New In Ubuntu ... I'm Studying Computer Science And I Would Like To Know To Install And Run Jgrasp On Ubuntu 13.04 ...

---

### Post by lbarowski on 2013-09-28
> **gadwin2 said:**
> Guys Im New In Ubuntu ... I'm Studying Computer Science And I Would Like To Know To Install And Run Jgrasp On Ubuntu 13.04 ...

Just download the jGRASP zip file, unzip it, and run .../jgrasp/bin/jgrasp .

The Java "bin" directory must be on your system PATH for it to run.

---

