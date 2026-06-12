---
title: "Java executables"
date: 2009-04-14
forum: Programming Talk
---

### Post by captainmnb on 2009-04-14
I've created a small Java program, and I currently run it with
```
java ClassName
```
or I suppose I could pretty easily package it in a JAR and run it with
```
java -jar whatever.jar
```

What I would like to do, however, is somehow make it so that I could put it in /usr/bin and run it straight from the terminal (it's a console-based program) with a single directory-independent call to the program's name.  Is this possible with Java (and for a beginner) on Ubuntu?

---

### Post by myrtle1908 on 2009-04-14
Somewhere along the line you need to refer to the *java* executable to run your program.  Why don't you create a shell script to run your program?  If the shell script is in your PATH then you can just call it from the terminal eg.

```
./runmyjavaprog.sh
```

---

