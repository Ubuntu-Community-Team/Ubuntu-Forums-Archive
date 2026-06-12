---
title: "what programs do i use to write Java, C, and Haskell in ubuntu?"
date: 2009-02-05
forum: Programming Talk
---

### Post by jiashen on 2009-02-05
Is there any program that come with Ubuntu 8.10 can write any of these code? or what should I install to be able to do so?

---

### Post by jespdj on 2009-02-05
For **Java**:

First, install a JDK (Java Development Kit). Sun's Java 6 JDK is probably the best one you can get:
```
sudo apt-get install sun-java6-jdk
```
[Sun's Java Tutorials](http://java.sun.com/docs/books/tutorial/) are a very good start to learn how to program Java and how to use the Java compiler and other tools in the JDK.

You might want to use an IDE. [NetBeans](http://www.netbeans.org) and [Eclipse](http://www.eclipse.org) are the two most popular IDEs. Both are primarily for Java (and both are written in Java themselves), but they also support other programming languages. NetBeans and Eclipse are in the Ubuntu repository, but the versions in the repository are old. It's better to download the newest versions from their websites and install those.

For **C**:

You'll want GCC (the GNU Compiler Collection) and the necessary other tools. Install the package **build-essential**:
```
sudo apt-get install build-essential
```
There are many IDEs that support C.

Read the sticky topics in this forum:

[Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming](http://ubuntuforums.org/showthread.php?t=1006666)
[Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662)

I don't know anything about Haskell. Try Googling for "Ubuntu Haskell" or "Linux Haskell" and you'll most likely find useful information.

---

### Post by Reiger on 2009-02-05
For Haskell you will (probably) want the Glasgow Haskell Compiler (GHC). You will often find yourself fiddling with its interactive shell ghci, in particular in awe of the simple ghci command:
```

:t <expr>

```
Where <expr> is any typed expression.

You can write Haskell code using any simple text editor, but you could also use a Haskell plugin for an existing IDE (there is one for Eclipse, a Java IDE anyways -- incidentally that one has plugins for C/C++ and PHP too).

Netbeans (judging by a quick, lazy google search) apparently lacks a Haskell plugin.

---

### Post by jiashen on 2009-02-05
thank you !!

---

