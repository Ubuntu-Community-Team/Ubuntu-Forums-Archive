---
title: "Java Uninstall/Fix Issues for Minecraft"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by mathematicallysplendid on 2012-06-27
Hello
I am fairly new to Ubuntu and I am confused out of my wits. I am generally a Windows user but I'd really like to use Ubuntu as my primary operating system. 
I play Minecraft often and I would like to play on this operating system, but I'm afraid java is giving me all sorts of trouble.

I believe I am running version:
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
I'm not sure if this is the correct version so I have tried to uninstall and reinstall because Minecraft won't go beyond the login page.
Through the Ubuntu Software Center I have tried to remove OpenJDK Java 7 Runtime by clicking the "Remove" button, but every time I remove this version OpenJDK Java 6 Runtime appears under the installed tab (just where Java 7 Runtime was)
When I remove Java 6, Java 7 appears just in its place. 

How do I remove/fix java and how can I get Minecraft to run?

I have Ubuntu 12.04 installed on my Asus (with Nvidia geforce 310m graphics card) 8 gigs of ram if information is of relevance. 

Thank you.

---

### Post by QIII on 2012-06-27
It could be that Minecraft does not play well with OpenJDK.  Unfortunately, some things don't.

See the Java wiki link in my signature.  I added a link in the Java 7 section called something like "Use webupd8.org's strikingly simple method" for installing Oracle Java 7.

You don't need to uninstall OpenJDK because they can coexist and you can switch between them.

Let me know if that helps.

(By the way, the webupd8 Java installer is the same one found in ubuntu-restricted-extras, so instead of adding the webupd8 ppa you can install ubuntu-restricted-extras instead of that step and then continue with the rest of the instructions.)

---

### Post by mathematicallysplendid on 2012-06-27
Thank you for the speedy reply, although Oracle Java 7 refuses to run Minecraft. 
[This post]("http://www.minecraftforum.net/topic/705738-minecraft-support-for-ubuntu/") on Minecraft forums explains using Sun Java. I will try this next. 
What is the difference between openJDK, Sun Java, and Oracle?

---

### Post by QIII on 2012-06-27
I strongly recommend against following the instructions in that link.  Java 6 has been replaced with Java 7.  Java 6 is old, has security problems and is due to reach its end of life in November.

OpenJDK 7 is the open source reference implementation of Oracle Java 7.

Oracle bought Sun and Sun Java is now Oracle Java.

Your problem may not be linked to Java at all if neither OpenJDK 7 nor Oracle Java 7 will work.

---

### Post by mathematicallysplendid on 2012-06-27
OpenJDK seems to get me beyond the login page and does load the launcher, however I am still receiving an error code referencing "glx"

something like "cannot find glx" or "glx does not exist"

---

### Post by QIII on 2012-06-27
That indicates a graphics issue, likely unrelated to Java other than by being referenced in the code for the game.

What graphics card are you using and which driver?

---

### Post by mathematicallysplendid on 2012-06-27
nvidia geforce 310m card (that came stock with the computer) 

how can I find which driver I am using?

---

