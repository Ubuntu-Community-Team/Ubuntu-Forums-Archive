---
title: "Java program"
date: 2009-04-23
forum: Programming Talk
---

### Post by keygiwawah on 2009-04-23
Is sun-java6-jdk or javac the compiler used in this thread?
[http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622)

Sorry this is probably a really stupid question, I'm just starting to learn about programming.

---

### Post by dwhitney67 on 2009-04-23
javac is the compiler that is available with the sun-java6-jdk package.

The 'jdk' stands for Java Development Kit.

---

### Post by Zugzwang on 2009-04-23
"javac" is the name of the command for compiling java programs. However, there do exists several java compilers out there, like the Sun's one or GCJ. "sun-java6-jdk" is the name of the Ubuntu package containing the Sun compiler. By running "update-alternatives ..." you tell the operating system which compiler to use when you just type "javac". Technically, all of these packages have some programs called "javac", but Ubuntu will pick the one selected.

---

### Post by keygiwawah on 2009-04-24
Thanks for the help

They really need to put the thank you button back

---

