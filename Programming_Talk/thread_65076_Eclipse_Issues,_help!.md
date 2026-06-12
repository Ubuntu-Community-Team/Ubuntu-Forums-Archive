---
title: "Eclipse Issues, help?!"
date: 2005-09-12
forum: Programming Talk
---

### Post by AlexanRO on 2005-09-12
I have Eclipse IDE running on 3 machines 2 of them are Debian stable branch and my main desktop of course is my beloved Ubuntu.  To my knowledge they are all configured identically 

Installed the following packages:
eclipse-javac (2.1.3-4)
eclipse-jdt (2.1.3-4)
eclipse-pde (2.1.3-4)
eclipse-platform (2.1.3-4)
eclipse-sdk (2.1.3-4)
eclipse-source (2.1.3-4)
junit (3.8.1.1-4)
libeclipse-jni (2.1.3-4)
liblucene-java (1.4.3-5)
liblucene-java-doc (1.4.3-5)
libswt2.1-gtk2-java (2.1.3-4)
libswt2.1-gtk2-jni (2.1.3-4)

the only exception is Ubuntu which

Installed the following packages:
sun-j2re1.5 (1.5.0+update04)

versus the other Debian machines

Installed the following packages:
sun-j2sdk1.4(1.4.2+05)

I said that to say this I am new to java and eclipse for that matter.  However, I do know that java is portable and that being said; my question is, if it works in one environment shouldn't it work the same in the other two as well?  I have included some screen shots, perahps there is something that I am overlooking hopefully someone more familiar with eclipse than I can reccomend where to start looking.

TIA for any sound advise

AlexanRO

---

### Post by user unknown on 2005-09-13
You definitively need the jdk (java development kit), not just the jre (java runtime environment) since you like to compile classes.
Get the javadocs too.
And get the sources.zip, which is usefull for debugging.

all available at java.sun.com.

---

### Post by AlexanRO on 2005-09-14
[QUOTE=user unknown]You definitively need the jdk (java development kit), not just the jre (java runtime environment) since you like to compile classes.
Get the javadocs too.
And get the sources.zip, which is usefull for debugging.

all available at java.sun.com.[/QUOTE]


Ok, First of all thank you for responding to my post.  Secondly I managed to install:

sun-j2se5.0-jdk-binary 1.5.0.04+debian-1.unofficial.sarge.1 (i386)
sun-j2se5.0-jdk-doc-en 1.5.0+debian-1.unofficial.sarge.1 (all)
sun-j2se5.0-jdk-doc-ja 1.5.0+debian-1.unofficial.sarge.1 (all)

on my Debian boxes.  However, I am unable to locate them when I try to download them from my current Ubuntu sources.  Would you happen to know where they are located?  I tried to add the deb sources of the deb repo that I was able to locate them in but I encountered some difficulty attempting to import the gpg key.  Lastly when I finally am able to download/install jdk on my Ubuntu machine are there any good docs that demonstrate how to configure Eclipse to use JDK?

Thanks again for your help.

AlexanRO

---

