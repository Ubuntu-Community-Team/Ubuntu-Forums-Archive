---
title: "Eclipse Java don't end process"
date: 2008-07-22
forum: Programming Talk
---

### Post by katsuma on 2008-07-22
Hi there, i would like to know why my eclipse, i tested europa and ganymede, don't end process like it should. I have to kill it manually.

I am using ubuntu 8.04 and tried the version of synaptic and latest version on eclipse.org. The 2 have the same problem however on the synaptic it opens 2 process, 1 with the name eclipse and the other with the name java. the both versions can't end process when i close eclipse.

Also it doesn't give any error, it just don't end process as usually should do.

Thank you. :KS

---

### Post by Diabolis on 2008-07-22
Eclipse is written in Java so It uses the JRE, thats why you see the Java process. If you use other applications written in Java, such as Jajuk, the JRE will keep running even when the application that started it (eclipse maybe) has been closed.

---

### Post by katsuma on 2008-07-22
yeah, but i checked and i don't have applications that require java to run...

when i run eclipse ganymede i see only one process, and when i terminate eclipse normally that process is still there, i have to kill it manually.
And also after i terminate eclipse in a normall way and dont kill the process, if i run again eclipse there will be 2 eclipse process, one of the eclipse before and this one that i actually run it now...

please i hope someone find a solution to this... many thanks :D

---

### Post by tinny on 2008-07-22
> **katsuma said:**
> yeah, but i checked and i don't have applications that require java to run...

when i run eclipse ganymede i see only one process, and when i terminate eclipse normally that process is still there, i have to kill it manually.
And also after i terminate eclipse in a normall way and dont kill the process, if i run again eclipse there will be 2 eclipse process, one of the eclipse before and this one that i actually run it now...

please i hope someone find a solution to this... many thanks :D

Are you talking about a process called "eclipse" or "javaw"? (or "java").

---

### Post by james.king@4act.com on 2008-11-03
I have noticed the same thing happening to me on Hardy 8.04 AMD64 using sun-java-6. 

When I close eclipse I still have both my Eclipse process running and my particular instance of java -jar <path to eclipse>/plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20080819.jar

If I run from a terminal the last few ouput lines are
2008-11-03 08:50:10.554::INFO:  jetty-6.1.11
2008-11-03 08:50:10.568::INFO:  Started SocketConnector@127.0.0.1:8502
2008-11-03 08:50:10.575::INFO:  Started SocketConnector@127.0.0.1:8602
2008-11-03 08:50:12.821::INFO:  Shutdown hook executing
2008-11-03 08:50:12.827::INFO:  Shutdown hook complete
2008-11-03 08:50:13.837::INFO:  Shutdown hook complete
2008-11-03 08:50:14.842::INFO:  Shutdown hook complete
2008-11-03 08:50:15.844::INFO:  Shutdown hook complete

but I never get my prompt returned. 

I just downloaded Eclipse a few days ago and I believe it may have been fine until I installed Aptana Studio. However, I cannot be sure because I used it very briefly before installing that plugin.

---

### Post by pedrobl on 2009-05-05
I still is happening, using intrepid on x386. It happens with all JDK I've tried: sun-6, openjdk, gcj...

Any ideas, anyone?

---

### Post by jespdj on 2009-05-05
> **Diabolis said:**
> If you use other applications written in Java, such as Jajuk, the JRE will keep running even when the application that started it (eclipse maybe) has been closed.
This is wrong, and this is not how Java works. When you start a Java program, a new Java process is started in which the JRE runs. If you start two Java programs, you'll have to processes each running their own JRE. There is not one JRE process that runs all your Java programs and that stays running when your Java program ends, as Diabolis suggests.

---

### Post by boteeka on 2009-08-18
Same problem here. I first noticed with AptanaStudio, but it happens to plain Eclipse too.

I have Jaunty 64bit installed. Any suggestions welcome.

---

### Post by james.king@4act.com on 2009-09-02
I have the same problem on Hardy 64 using sun java 1.6.0_16 and eclipse Galileo. I have had it on previous versions of java/eclipse for almost a year now. I have not paid close attention to it because I rarely actively use either and simply became used to killing the process manually (like a well trained monkey).

---

### Post by james.king@4act.com on 2009-09-02
Found this in launchpad.
[https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/68714](https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/68714)

Seemed to do the trick for me. I uninstalled  at-spi.

---

