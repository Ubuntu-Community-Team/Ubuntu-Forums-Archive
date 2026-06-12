---
title: "java question"
date: 2010-11-15
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-11-15
Howdoi compile a java program with gcj?

---

### Post by SevenMachines on 2010-11-15
gcj probably looks familiar if you've used gcc, g++, etc.

Simple example...

HelloWorld.java:
> public class HelloWorld {
    public static void main (String[] args) {
    System.out.println ("Hello World!");
    }
}Compile and link...
> $ gcj --main=HelloWorld -o HelloWorld HelloWorld.java 
$ ./HelloWorld 
Hello World!using --main= to specify which file has the 'main' entry point is the important new thing.

As usual with gnu compilers theres a lot of other options to do pretty much everything in man gcj :*)

---

### Post by SevenMachines on 2010-11-15
Just a p.s. addition, if you want to compile .java files into .class bytecode instead of directly into native code...
> $ gcj  -C  HelloWorld.java 
$ jclassinfo --methods --general HelloWorld.class 
[CLASS INFORMATION]                                                             
public class HelloWorld extends java.lang.Object
Compiled from HelloWorld.java
Requires: Java VM unknown or higher
[METHODS]
public HelloWorld() 
public static void main(java.lang.String[]) 


---

