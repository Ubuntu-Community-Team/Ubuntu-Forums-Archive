---
title: "conferencing software using java media framework"
date: 2008-04-11
forum: Packaging and Compiling Programs
---

### Post by dexter.deepak on 2008-04-11
i have tried making a java program using jmf api which can be used to broadcast / receive a live stream. now the thing is that i want a debian installer for this. , or even an install script would do. my purpose is to install jmf, install java, and set the classpath automatically in one go.

i have no experience of making even a windows installer...so i would be grateful if someone guides me to have a deb/exe file creation .


thanks in anticipation.

---

### Post by Zugzwang on 2008-04-11
Try google for "Debian Package". The results 3-7 (when I tried it) tell you a little bit about making Debian packages.

However, your package *should not* modify the classpath globally. Instead, add dependencies for Java, JMF & create a script for executing your program which calls Java with the -cp option accordingly.

Packaging for Windows is more complicated since you have external requirements (Java, JMF). A lot of enterprise software bundles its own JRE with the software. Maybe you want to go that way to *OR* use some installer-generator program that creates an installer for you that searches for JMF & a JRE prior to installation and writes that information somewhere in the destination directory. Then you just need a custom caller and you're done.

Alternatively, you may drop the project of building DEBs and Windows installation packages and use Java WebStart instead. This should be *far* easier (but require the users to have a JRE installed).

---

### Post by dexter.deepak on 2008-04-11
>> Alternatively, you may drop the project of building DEBs and Windows installation packages and use Java WebStart instead. This should be *far* easier (but require the users to have a JRE installed).

would you please explain it a bit further..i dont know how to use webstart..though i am having it on my system

---

### Post by Zugzwang on 2008-04-12
> **dexter.deepak said:**
> would you please explain it a bit further..i dont know how to use webstart..though i am having it on my system
[http://en.wikipedia.org/wiki/Java_Web_Start]("http://en.wikipedia.org/wiki/Java_Web_Start") - All the information & links you need

---

### Post by dexter.deepak on 2008-04-12
thanks for the link.
but i must admit that i could only derive one thing from all the pages i visited - that i CAN use javawebstart...but i could not understand HOW to do it...
this is because i have my semester exams over my head and i have already devoted full of my semester , studying JMF to make 2nd yr. engg. project...it was at last moment that i decided to convert it into a web project.

so can you please help me getting HOW the things are working ... i know i can google it out , but for the time being i cannot afford that time (that too on a dialup internet connection !!)
please ...this is a humble request.

---

### Post by Zugzwang on 2008-04-14
There's a policy on homework here, so I can only point to a tutorial stating how to make WebStart applications:

[http://java.sun.com/docs/books/tutorial/deployment/webstart/deploying.html]("http://java.sun.com/docs/books/tutorial/deployment/webstart/deploying.html")

---

### Post by dexter.deepak on 2008-04-14
thanks a lot ...that helped me get the point

---

