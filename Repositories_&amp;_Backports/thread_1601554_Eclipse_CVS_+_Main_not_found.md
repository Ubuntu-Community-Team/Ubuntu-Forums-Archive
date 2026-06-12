---
title: "Eclipse CVS + Main not found"
date: 2010-10-20
forum: Repositories &amp; Backports
---

### Post by nova47 on 2010-10-20
I'm working in a group for a project so naturally we have set up CVS. During the course of our work and over several different projects CVS seems to enjoy vomiting on itself and randomly displaying a red ! next to our project name. After this occurs whenever any of us, on any machine, try to run our project the Java Virtual Machine Launcher displays an error pop up saying Could not find the main class: Main. Program will exit. (The main method is in a class I called Main.) And of course it prints the following out to stderr:

java.lang.NoClassDefFoundError: Main
Caused by: java.lang.ClassNotFoundException: Main
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
Exception in thread "main" 

There doesn't seem to be any rhyme or reason we just go to bed, wake up, and it's there. If we copy and paste all our classes to a local folder it works just fine so it is not an issue with code it is something with CVS. Oddly enough sometimes it will just go away randomly. We haven't been able to figure out what the cause of either the problem or it randomly fixing itself is. Any ideas?

---

### Post by kbryk on 2010-10-21
Sorry I don't have a solution but Eclipse from what I remember is very particular when it comes to workspaces. By that I mean if I were to compile my source on a workspace at school and then copy those files over to a different workspace, like a home, Eclipse would give me lots of errors.

Since it does happen variably try to watch what you do differently or if it happens on a specific computer.

---

### Post by nova47 on 2010-10-25
I found the problem. We had originally made another folder other than src. CVS added this to our build path found by right clicking on the project folder -> properties -> Java Build Path -> Source. We deleted the erroneous folder and now it works again.

---

