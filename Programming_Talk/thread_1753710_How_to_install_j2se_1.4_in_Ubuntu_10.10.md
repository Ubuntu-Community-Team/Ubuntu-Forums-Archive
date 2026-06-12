---
title: "How to install j2se 1.4 in Ubuntu 10.10 ?"
date: 2011-05-09
forum: Programming Talk
---

### Post by rdst on 2011-05-09
I'm using Eclipse with Java version is Open JDK 1.6.
However, my project requires Java 1.4, so I need to install another version of Java (*if I set compiler compliance level 1.4 in Eclipse, Java 1.4 should be installed, is it right?*). I downloaded .bin file from [here]("http://java.sun.com/products/archive/j2se/1.4.0/index.html") but I have had a problem with running .bin file.
I did step by step as in instruction note. I've always gotten this message:

> The download file appears to be corrupted.  Please refer to the Troubleshooting section of the Installation Instructions on the download page for more information. Please do not attempt to install this archive file.

If I download java version 1.5 or 1.6 from the same above website, I can run .bin file successfully. But my project is only compatible with Java 1.4. So I really need to install Java 1.4 in my Ubuntu.
Please instruct me step by step how to install Java 1.4 in Ubuntu 10.10 and how to config Eclipse to work with this version as well !

Appreciate any help !

---

### Post by trozamon on 2011-05-09
> **rdst said:**
> But my project is only compatible with Java 1.4.
 
Here's the thing: Java 1.6 has all the methods that 1.4 has; and project that needs 1.4 will run with any version beyond 1.4 also. Thus, just install 1.6.

---

### Post by kvant_doan on 2011-05-09
Hi guys,

I think you should remove OpenJDK and reinstall JDK 1.6 

[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

Because in my project, I also have some problems with OpenJDK.

Hope this help.

---

### Post by stchman on 2011-05-09
> **rdst said:**
> I'm using Eclipse with Java version is Open JDK 1.6.
However, my project requires Java 1.4, so I need to install another version of Java (*if I set compiler compliance level 1.4 in Eclipse, Java 1.4 should be installed, is it right?*). I downloaded .bin file from [here]("http://java.sun.com/products/archive/j2se/1.4.0/index.html") but I have had a problem with running .bin file.
I did step by step as in instruction note. I've always gotten this message:



If I download java version 1.5 or 1.6 from the same above website, I can run .bin file successfully. But my project is only compatible with Java 1.4. So I really need to install Java 1.4 in my Ubuntu.
Please instruct me step by step how to install Java 1.4 in Ubuntu 10.10 and how to config Eclipse to work with this version as well !

Appreciate any help !

Java 1.6 is compatible with Java 1.4.  Install Java 1.6 SDK.

```

[COLOR=Black][FONT=monospace]sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin[/FONT][/COLOR]

```

---

### Post by slavik on 2011-05-11
java 1.6 is compatible with 1.4 only if there is no deprecated api usage that was removed and 1.4 has incorrect behavior that does not work in 1.6

---

