---
title: "Weird .class error?"
date: 2011-04-18
forum: Packaging and Compiling Programs
---

### Post by linc186 on 2011-04-18
Running classes through the terminal has never been a problem for me....but now it is. The command java packagehere/Classhere always worked, but it suddenly decided to just not work anymore. Rather than define a cp (I'm too lazy) I just run the .class from its directory, but the command isn't working. I tried putting the .class into a folder and then running it, but that didn't work either. Here's the error message:
lincoln@lincoln-Inspiron-537:~$ cd Desktop
lincoln@lincoln-Inspiron-537:~/Desktop$ cd java
lincoln@lincoln-Inspiron-537:~/Desktop/java$ java game/Game
Exception in thread "main" java.lang.NoClassDefFoundError: game/Game
Caused by: java.lang.ClassNotFoundException: game.Game
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: game/Game. Program will exit.
lincoln@lincoln-Inspiron-537:~/Desktop/java$ 

Any help is appreciated. Thanks!

---

### Post by andrewc6l on 2011-04-19
The official syntax would be:

java packagename.Classname

(note the . instead of /). Make sure you're in the parent of packagename, and your class has the package packagename.

---

### Post by linc186 on 2011-04-19
> **andrewc6l said:**
> The official syntax would be:

java packagename.Classname

(note the . instead of /). Make sure you're in the parent of packagename, and your class has the package packagename.

still doesn't work. Thanks, though.

---

