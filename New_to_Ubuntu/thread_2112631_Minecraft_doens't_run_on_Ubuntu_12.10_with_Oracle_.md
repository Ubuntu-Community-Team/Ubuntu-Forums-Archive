---
title: "Minecraft doens't run on Ubuntu 12.10 with Oracle Java"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by chron3 on 2013-02-05
I installed Oracle Java 6 Update 39 and tried to run Minecraft. After logging in, I just get a black screen and the following error message is displayed in the terminal:

```
Exception in thread "Minecraft main thread" java.lang.ExceptionInInitializerError
	at net.minecraft.client.Minecraft.a(SourceFile:205)
	at asq.a(SourceFile:56)
	at net.minecraft.client.Minecraft.run(SourceFile:515)
	at java.lang.Thread.run(Unknown Source)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
	... 4 more
```

I tried using the Open JDK, but it doens't work either.

---

### Post by chron3 on 2013-02-05
This helped:

[http://askubuntu.com/questions/177996/how-do-i-patch-minecrafts-lwjgl-libraries]("http://askubuntu.com/questions/177996/how-do-i-patch-minecrafts-lwjgl-libraries")

---

