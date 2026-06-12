---
title: "Eclipse source code problem"
date: 2011-05-28
forum: Programming Talk
---

### Post by querman on 2011-05-28
Hello there!
I'm using ubuntu natty and i'm install eclipse galileo and jdk version "1.6.0_24".
When i run eclipse and left click+CTRL some code like System it's not open jdk source code and show this screen and say Source Not Found what is the problem?

[IMG]http://img97.imageshack.us/img97/5245/screenshotzra.png[/IMG]

---

### Post by simeon87 on 2011-05-28
You are attempting to view a .class file, which is not a Java source code file. If you want to see the source, you have to download the source code somewhere and configure some settings in Eclipse to attach the source code to those .class files.

Generally this error message occurs when you're trying to view code from libraries of which you only have the .class files.

---

### Post by javaexp on 2013-02-09
I have put a blog post to show how we can [attach the source code for JDK]("http://www.javaexperience.com/eclipse-attach-jdk-source-in-java-application/") or any third party library in Eclipse.

---

