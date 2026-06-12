---
title: "Question about setting up Geany and Java"
date: 2012-02-28
forum: Programming Talk
---

### Post by Ir0nMa1deN on 2012-02-28
[FONT=Arial Narrow][SIZE=3]I just installed Geany on Ubuntu 11.10 and I'm having trouble setting it up to run a small GUI applet. I tested a basic console app and it worked fine, but whenever I try to compile the GUI app, I get the following error:
[SIZE=2][COLOR=DarkRed]Exception in thread "main" java.lang.NoSuchMethodError: main
[SIZE=3][COLOR=Black]In the compiler, it says "/bin/sh: javac: not found"
From the looks of it, java isn't installed properly (i checked using whereis javac in the terminal and the it just said javac:) So I guess my question is, how should I install Java (I know there's a bunch of different ones out there like OpenJDK or the IcedTea one) and how can I configure Geany to be able to run this GUI app?
[/COLOR][/SIZE]
[/COLOR][/SIZE]
[/SIZE][/FONT]

---

### Post by Ir0nMa1deN on 2012-02-28
Hmm I found out that Geany might not support GUI applets. Looks like I'll be trying some other IDE

---

### Post by Some Penguin on 2012-02-29
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
Contains information on installing a number of variants.  My preference is to stick with the Sun (well, now Oracle) reference implementations, specifically version 6 and not 7.

---

### Post by r-senior on 2012-02-29
I like Geany as a lightweight IDE for C but I wouldn't use it for Java. Netbeans and Eclipse have all the useful plugins for Maven, JUnit, etc.. and support refactoring, generation of getters/setters, etc..

I've always preferred Netbeans because it works out of the box. But (a) it's no longer in the repositories and (b) I got tired of poor font rendering. So I'm using Eclipse again (specifically SpringSource Tool Suite because I do a lot of Spring stuff).

Like SomePenguin, I've tended to prefer the reference implementations of Java, but I've been using OpenJDK 1.7 for the past couple of months and haven't run into any problems at all. This is with fairly involved stuff - Spring/Hibernate, JSR-303 validation, AOP, declarative transactions and Spring MVC with AJAX. It's been fine.

---

### Post by Ir0nMa1deN on 2012-02-29
Well as you can probably tell by now my knowledge of Linux and programming isn't very advanced so this is too much for me right now. I'll probably stick to JCreator for Windows 7 since that's what I'm using at school. I'll check out Eclipse and if it works great, if not then no problem. Thanks for the replies anyway

---

### Post by r-senior on 2012-03-01
Eclipse can seem large and complex and it has its idiosyncracies but you shouldn't reject it because you are a beginner/intermediate programmer. IMO you should try to get used to it because it's the most commonly used IDE for Java projects (including those with Windows desktops).

It's true that using Geany, or even Gedit and the command line for small projects helps you to understand classpaths and so on. But for real work in Java, the plugins and features of an IDE like Eclipse help you. They don't make your life more difficult.

If I was teaching a complete novice, I might do some stuff from the command line to start with but I'd move onto Eclipse pretty quickly. It's not a tool that's only for advanced programming.

---

