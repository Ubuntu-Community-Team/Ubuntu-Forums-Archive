---
title: "launching a webpage from an application"
date: 2007-06-18
forum: Programming Talk
---

### Post by Greenmanspirit on 2007-06-18
I am writing a program for work and we want to be able to link our application to content online.  Are there any easier ways to do this other then to write a script to see what browser is installed and then do that browsers specific command.  

On of my issues is that we do not want to require a certain shell or a certain browser, which is the right way to do it, i just dont know how to program for it.  

The application is written in java, but I am more then willing to learn shell scripting if thats what needs done.

---

### Post by tr333 on 2007-06-18
a quick google found [http://www.javaworld.com/javaworld/javatips/jw-javatip66.html](http://www.javaworld.com/javaworld/javatips/jw-javatip66.html), which looks like what you want.

---

### Post by Greenmanspirit on 2007-06-18
Thats generally what I want to do, but its working off the assumption that netscape is there.  Is it a fairly standard thing for unix/linux to have netscape installed, or at least a netscape script that invokes another browser?

PS. I officially stink at google searches

---

### Post by tr333 on 2007-06-18
[http://www.centerkey.com/java/browser/]("http://www.centerkey.com/java/browser/")
that seems to extend what was in the previous link to include multiple browsers.

you could also try looking at the [JDesktop Integration Components](https://jdic.dev.java.net/) that aim to provide desktop integration for java.

---

### Post by Greenmanspirit on 2007-06-18
Thanks, the barebones launcher thing is what i originally had in mind for this, but I was hoping there would be some shell functionallity to do it more implicitly.  Thanks again. :)

---

### Post by tr333 on 2007-06-18
> **Greenmanspirit said:**
> Thanks, the barebones launcher thing is what i originally had in mind for this, but I was hoping there would be some shell functionallity to do it more implicitly.  Thanks again. :)

shell functionality would just make it platform-dependent, removing one of the major benefits of java.

---

### Post by Ragazzo on 2007-06-19
If you use Java 6, there is [http://java.sun.com/javase/6/docs/api/java/awt/Desktop.html#browse(java.net.URI)](http://java.sun.com/javase/6/docs/api/java/awt/Desktop.html#browse(java.net.URI))

---

### Post by Greenmanspirit on 2007-06-19
> **tr333 said:**
> shell functionality would just make it platform-dependent, removing one of the major benefits of java.

To do this kind of command you have to test what the operating system is in order to send the correct command to the OS.  What I ment by shell thing would be a command or set of commands I could tell java to send to the OS under the unix/linux section of my code, rather then having the loop to see what the user has installed because that leads to the problem, well what if the user doesnt have a certain program. :-?

> **Ragazzo said:**
> If you use Java 6, there is [http://java.sun.com/javase/6/docs/api/java/awt/Desktop.html#browse(java.net.URI)](http://java.sun.com/javase/6/docs/api/java/awt/Desktop.html#browse(java.net.URI))

Wow thats exactly what I was looking for, though Im not sure if Im allowed to use 1.6 only things yet.

---

