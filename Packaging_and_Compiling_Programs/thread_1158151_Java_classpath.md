---
title: "Java classpath"
date: 2009-05-13
forum: Packaging and Compiling Programs
---

### Post by doug804 on 2009-05-13
I am having a problem correctly setting the classpath variable.

I am running Ubuntu 8.10,
java version "1.5.0_16"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_16-b02)
Java HotSpot(TM) Client VM (build 1.5.0_16-b02, mixed mode, sharing)

I had been using the standard OpenJDK-6 but wanted to downgrade to use java grammer 1.5

I used the following command to change the JDK used.
sudo update-alternatives --config java

I have set the classpath with 
set CLASSPATH =$CLASSPATH:/home/cdouglas/plaggie:/home/cdouglas/plaggie/java_cup/java_cup/runtime/
and I get the following error
Exception in thread "main" java.lang.NoClassDefFoundError: java_cup/runtime/lr_parser
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:164)
    at plag.parser.plaggie.Plaggie.main(Plaggie.java:622)


It looks like an error in my classpath, so I tried to complie and run a simple HelloWorldApp and I cant

I'm new to Linux is there an easy way to set the classpath from the Terminal?

---

### Post by doug804 on 2009-09-18
I figured it out. The problem was with the program not my Linux installation.
 
Thanks to all that looked at the problem and got stumped

---

