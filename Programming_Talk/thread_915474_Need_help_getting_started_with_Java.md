---
title: "Need help getting started with Java"
date: 2008-09-09
forum: Programming Talk
---

### Post by connor on 2008-09-09
I have a programming class that is using Java, but I don't really know how to get started. What do I need to download to start compiling and running Java programs. I'm ok with writing c++ programs in a text editor and then compiling and running them in the shell, but I don't know how to start doing this with Java.


Thanks!
Connor

---

### Post by Rocket2DMn on 2008-09-09
Moved to Programming Talk.

BTW, you stole my name.  Thanks.
:guitar:

You need the java compiler, simply referred to as javac, and it comes with build-essential
```
sudo apt-get install build-essential
```
Then to run
```
java <name>
```

---

### Post by LaRoza on 2008-09-09
Rocket2DMn: I don't think that will work, unless the've changed build-essential.

[http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622)

---

### Post by tinny on 2008-09-09
> **LaRoza said:**
> Rocket2DMn: I don't think that will work, unless the've changed build-essential.

[http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622)

@LaRoza, I notice you dont have any recommendations for a text editor setup for Java. I would think that gedit would be good for beginners.

Perhaps this How to is worth referring too?
[http://ubuntuforums.org/showthread.php?t=414544](http://ubuntuforums.org/showthread.php?t=414544)

---

### Post by u-slayer on 2008-09-10
I was in the same situation recently and here's what I did.

Get Java 6 made by Sun. Ubuntu's java thingy sucks...


```
	
/usr/lib/jvm/java-6-sun/bin/javac -classpath filepath -d bindir filepath
/usr/lib/jvm/java-6-sun/bin/java filename

```

Replace vars with your filenames:

example filepath=test.java
bindir=/home/$USER
filename=test

---

### Post by Zugzwang on 2008-09-10
> **u-slayer said:**
> Get Java 6 made by Sun. Ubuntu's java thingy sucks...


That's a bad advice. If installed correctly, you'll precisely get the JDK with the Ubuntu package manager. And in that case you won't have these path problems which may for example cause build with "ant" to fail (without changing the Makefile, which is beyond the capabilities of a beginner) - not to mention simpler updates.

It appears as if you have bad experience with the Ubuntu package management w.r.t. Java since you forget to call the update-alternatives command. :KS

---

### Post by Reiger on 2008-09-10
When you get further into Java you will likely want an IDE, there exist mutliple ones -- among those (the more popular?) is Eclipse. Eclipse works well for developing Java though it is a bit of resource hog (and considerably more so on Ubuntu than it seem to be on Windows... <_<). IDE's will take away much of the hassle of writing syntactically good code; and at times even help with semantics; apart from giving you a managed testing environment which is a godsend if you inadvertently manage to make your program loop infinetely for instace...

---

### Post by jespdj on 2008-09-10
Install Sun Java 6 from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```
This will get you the JDK (Java Development Kit), which includes the Java compiler and other tools.

For editing Java source files, you can just use gedit (the standard Ubuntu text editor), it has source code highlighting for Java, or you can use something more fancy such as Geany (a simple lightweight IDE) or Eclipe or NetBeans (the two most popular Java IDEs).

For Java tutorials, start at Sun's [Java Tutorials](http://java.sun.com/docs/books/tutorial/) page.

---

### Post by Rocket2DMn on 2008-09-10
Thanks LaRoza, I totally forgot about actually installing JVM/JRE.  It's been a long week :)

---

### Post by The Cog on 2008-09-10
After installing Suns JDK. I suggest you install geany as a good fast and simple editor, with a compile button.
> sudo apt-get install geany

---

