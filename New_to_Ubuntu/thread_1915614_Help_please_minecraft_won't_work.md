---
title: "Help please minecraft won't work"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by bigg132 on 2012-01-26
Hi, i am new to ubuntu and have tried to install minecraft. I have downloaded java and he linux version of minecraft and tried to open it. To cut the story short basically after i log it comes up with this error message.

Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [EMAIL="support@mojang.com"]support@mojang.com[/EMAIL].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 1/26/12 6:44 PM

Minecraft: Minecraft 1.1
OS: Linux (i386) version 3.0.0-15-generic
Java: 1.6.0_23, Sun Microsystems Inc.
VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:230)
    at net.minecraft.client.Minecraft.run(SourceFile:648)
    at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT b354f3e7 ----------


help would be greatly appreciated! 
thanks.

---

### Post by I8NY on 2012-01-26
you have the wrong type of java.  ubuntu comes with JDK that is opensource but it doesn't work with all java apps.  go the the package manager and search for "sun java" and install "sun-java6-jre"

---

### Post by Paqman on 2012-01-26
> **I8NY said:**
> you have the wrong type of java.  ubuntu comes with JDK that is opensource but it doesn't work with all java apps.  go the the package manager and search for "sun java" and install "sun-java6-jre"

This is not correct.
[LIST=1]
[*]OpenJDK works fine with Minecraft. I use it myself.
[*]Sun have pulled the licence for Java 6, and are transitioning to Java 7, which is based on OpenJDK anyway
[/LIST]

Bottom line is that OpenJDK is the right thing to have on your system. Bigg132, try downloading Minecraft again, maybe you got a bad download. Your error message does seem to be related to Java itself though. How and where did you install it from?

---

### Post by anewguy on 2012-01-26
You may also want to have someone move the thread to the ubuntu games and leisure forum - you'll probably get way more help over there.

Dave ;)

---

### Post by I8NY on 2012-01-27
> **Paqman said:**
> This is not correct.
[LIST=1]
[*]OpenJDK works fine with Minecraft. I use it myself.
[*]Sun have pulled the licence for Java 6, and are transitioning to Java 7, which is based on OpenJDK anyway
[/LIST]

Bottom line is that OpenJDK is the right thing to have on your system. Bigg132, try downloading Minecraft again, maybe you got a bad download. Your error message does seem to be related to Java itself though. How and where did you install it from?
You are right about 1. when I first started playing Minecraft in Ubuntu it didn't work with OpenJDK but now it does. (I just tested it ;))  Bigg132, also try to start minecraft with "java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame" and make sure you have your video card driver installed.

---

