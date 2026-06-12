---
title: "[SOLVED] Is there any java compiler on Ubuntu?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by zirun292 on 2008-10-28
i try to compile for the first time in my computer and it says :-

hazim@hazim-desktop:~$ javac
The program 'javac' can be found in the following packages:
 * gcj-4.1
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * ecj
 * jikes-sun
 * openjdk-6-jdk
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * jikes-kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found

which one do i have to install?

---

### Post by Crafty Kisses on 2008-10-28
Eclipse.

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by gvoima on 2008-10-28
I recommend installing the sun java packages. So pick the ver.5 or 6. Whatever suits your needs :)

sun-java5/6-jdk (Sun java development kit). It is The java-language developer. So it would be recommended to use those packages.

---

### Post by jerome1232 on 2008-10-28
I'm just guessing here but could it be this program
javacc - A parser generator for use with Java


I found it by doing
```
apt-cache search javac
```

---

### Post by gvoima on 2008-10-28
> **jerome1232 said:**
> I'm just guessing here but could it be this program
javacc - A parser generator for use with Java


I found it by doing
```
apt-cache search javac
```Yeah well, that's a parser generator, not a compiler :)

java compiler (javac) is a part of the Sun microsystems development kit (sun-javax-jdk).
So it gets installed when you install the jdk. Also other binarys like the runtime environment etc. gets installed.

---

### Post by jerome1232 on 2008-10-28
I guess it was a bad guess then :-\"

Then again I thought java wasn't compiled it ran in a "virtual machine" type of deal to make it cross-platform. 

Let me note I don't pretend to know anything about java other than it's a programming language that works well across platforms.

---

### Post by gvoima on 2008-10-28
> **zirun292 said:**
> i try to compile for the first time in my computer and it says :-

hazim@hazim-desktop:~$ javac
The program 'javac' can be found in the following packages:
which one do i have to install?

If you are interested in java development, i recommend that you google some java tutorials :)
[http://java.sun.com/]("http://java.sun.com/") is also a good place to know.

---

### Post by gvoima on 2008-10-28
> **jerome1232 said:**
> I guess it was a bad guess then :-\"
Atleast you tried! Some don't even bother :)

---

### Post by zirun292 on 2008-10-28
i think i am gonna pick the "sun-java6-jdk". 
and thanks guy!!! :KS

---

### Post by Xiong Chiamiov on 2008-10-28
> **zirun292 said:**
> 
which one do i have to install?

None.  If you want a java compiler, however, any of those will provide one for you.  There are many choices due partly to different versions of Java (5 and 6), as well as some open-source implementations.

sun-java6-jdk is the most common, which seems to be what you chose.

> **Codename said:**
> Eclipse.

[http://www.eclipse.org/](http://www.eclipse.org/)

Eclipse isn't a Java compiler, it's an editor.  I'm sure you know that; I'm just pointing it out for people who come across this thread.

> **jerome1232 said:**
> 
Then again I thought java wasn't compiled it ran in a "virtual machine" type of deal to make it cross-platform. 


Java code is generally compiled, although it can be just-in-time compiled, which is similar to what Python does (at least, CPython).

---

### Post by zirun292 on 2008-11-03
i already try the java-6dk and it works!!! 
and i also try the eclipse but it doesn't work. i dont know why?:confused:

but thanks for the help guys. i've been searching this java compiler for a long time.

---

### Post by igotnoluck on 2008-11-03
just download the eclipse and unpack it. then all you need to do is run the ./eclipse command.

---

### Post by zirun292 on 2008-11-04
Anyway i don't want to use Eclipse
I think it is not that good. I think so.
By the way, Thanks for your help :guitar:

):P

---

