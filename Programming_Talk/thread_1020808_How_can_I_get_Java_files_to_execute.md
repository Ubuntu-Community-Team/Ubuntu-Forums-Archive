---
title: "How can I get Java files to execute?"
date: 2008-12-24
forum: Programming Talk
---

### Post by lkrubner on 2008-12-24
I'm confused about Java on my machine (running Ubuntu 6.06).  If I open a terminal and type

which java

I get this response:

/usr/bin/java

so it seems to be installed. And I've opened the Synaptic Package Manager and updated everything I could that looked Java related. (Though if you search for "Java" a lot of junk comes back.)

Here is the problem: I have downloaded several files that end with ".jnlp" but when I click them, nothing happens. I've told the coomputer to use /usr/bin/java to open these files, but something isn't working right. 

Any ideas?

---

### Post by lkrubner on 2008-12-24
I have Java 1.4.2 on my machine. I read here that all I need is 1.4 and I should be able to open jnlp files:

[http://java.sun.com/developer/technicalArticles/Programming/jnlp/](http://java.sun.com/developer/technicalArticles/Programming/jnlp/)

Another question: that article is from 2002. Why is  1.42 the newest version of Java that I can get from the Synaptic Package Manager? Shouldn't I be able to at least get version 1.5?

---

### Post by Ruhe on 2008-12-24
Usually jnlp act as link on web pages.
Try to click on links on this demo page - [http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html](http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html)

If you will not see any results we'll try to find the problem.

---

### Post by Ruhe on 2008-12-24
> Another question: that article is from 2002. Why is 1.42 the newest version of Java that I can get from the Synaptic Package Manager? Shouldn't I be able to at least get version 1.5?

Maybe because 6.06 is no longer supported?

---

### Post by CptPicard on 2008-12-24
Java 1.4 is ancient, and the Sun JDK available in the repos is 1.6. I have a hunch you're trying to use the GNU version of Java, which you should just forget about, it's way behind the curve.

Also, Java Web Start is just a specific way to launch stuff from websites... running ordinary java stuff usually means just using the "java" command on either a class file with "main" or a .jar file.

---

### Post by catchmeifyoutry on 2008-12-24
Is this for some java program you wrote yourself (this being the "Programmer Talk" forum)? I haven't done a lot with java it was part of some of my courses, but you could maybe first try to run a program from the terminal and see if that works.

```

>edit MyProgram.java
>javac MyProgram.java
>java MyProgram

```

See [http://java.sun.com/developer/onlineTraining/Programming/BasicJava1/compile.html](http://java.sun.com/developer/onlineTraining/Programming/BasicJava1/compile.html)

Does it run now?

---

### Post by lkrubner on 2008-12-24
> **Ruhe said:**
> Usually jnlp act as link on web pages.
Try to click on links on this demo page - [http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html](http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html)

If you will not see any results we'll try to find the problem.

When I click the items on that page, it asks me if I want to open it or download it. No matter what I do, it does not run. I can try to open it in FireFox or with Java, but neither seems to work. If I download the file and then try to open it, I have the same problem. FireFox does not open the files, but only asks me, again, if I want to open or download the file. If I try to use /usr/bin/java, then nothing happens.

---

### Post by lkrubner on 2008-12-24
> **Ruhe said:**
> Maybe because 6.06 is no longer supported?

I thought Synaptic Package Manager showed me everything that was available from the Ubuntu repository, regardles of which version of Ubuntu I was running? 

If I switch to a terminal and run "apt-get install" I'm still calling from the same repository as Synaptic Package Manager, right? And apt-get doesn't care what version of Ubuntu I have installed, does it?

---

### Post by lkrubner on 2008-12-24
> **CptPicard said:**
> Java 1.4 is ancient, and the Sun JDK available in the repos is 1.6. I have a hunch you're trying to use the GNU version of Java, which you should just forget about, it's way behind the curve.

Also, Java Web Start is just a specific way to launch stuff from websites... running ordinary java stuff usually means just using the "java" command on either a class file with "main" or a .jar file.

If I open Synaptic Package manager and search for "Sun JDK" or "java-lang" or simply "JDK" nothing comes back that has a 1.6 attached to it as a version number. Everything seems to be free replacements for Sun stuff. I can't find the Sun stuff.

---

### Post by lkrubner on 2008-12-24
> **catchmeifyoutry said:**
> Is this for some java program you wrote yourself (this being the "Programmer Talk" forum)? I haven't done a lot with java it was part of some of my courses, but you could maybe first try to run a program from the terminal and see if that works.

```

>edit MyProgram.java
>javac MyProgram.java
>java MyProgram

```


Interesting idea. I ran the command from the command line and got the following errors:

```
lkrubner@programmerpc3:~/Desktop$ java mg.jnlp
Exception in thread "main" java.lang.NoClassDefFoundError: mg.jnlp
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: mg.jnlp not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
```


As I think I mentioned before, I wanted to learn JavaFX, and I started running into roadblocks. If I can get ordinary Java to work on my machine, then I'd like to steal the hacks that make it work on a Mac and so make JavaFX work on my machine. 

But first I have to get ordinary Java to work.

---

### Post by slavik on 2008-12-24
umm, has anyone tried javaws being that jnlp are for java webstart?

---

### Post by lkrubner on 2008-12-25
> **Ruhe said:**
> Maybe because 6.06 is no longer supported?

I see, the repositories are specific to a version.

---

### Post by lkrubner on 2008-12-25
> **slavik said:**
> umm, has anyone tried javaws being that jnlp are for java webstart?

Thanks, that worked. I set ".jnlp" files to open with 

/usr/bin/javaws

and that seems to work.

---

### Post by jespdj on 2008-12-25
> **lkrubner said:**
> I thought Synaptic Package Manager showed me everything that was available from the Ubuntu repository, regardles of which version of Ubuntu I was running?
No, it does not. There is a separate repository for each Ubuntu release, and once a release is not supported anymore, Canonical doesn't update its repository anymore. Eventually the repository of an obsolete release might be taken offline.

---

