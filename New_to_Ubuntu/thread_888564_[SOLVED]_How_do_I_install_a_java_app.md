---
title: "[SOLVED] How do I install a java app?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by t0p on 2008-08-13
I want to install a java app, the java client for an anonymizing service Your Freedom.  So, I first installed openVPN (from the repos) as instructed by the Your Freedom webpage.  Then I downloaded the Your Freedom zip archive, and extracted it.  Then I sat and looked at the list of files and wondered what to do. :confused:

Here's the list of extracted files (which I extracted into a directory called sandbox):

```
t0p@ubunty:~/Desktop/sandbox$ ls
CHANGES.txt    HOW-IT-WORKS.txt     iconopened.ico         README.txt
CLIENTVERSION  ICE_JNIRegistry.dll  iconopenedwide.ico     systray4j.dll
COPYING        iconclosed.ico       KNOWNBUGS.txt          winlaf.dll
freedom.jar    iconfailing.ico      LatteLibWin-3.0.0.dll

```

I recognize **freedom.jar** as being the executable.  But I don't know about the other stuff. Where does it go?  And I see **.dll** files, which I always thought were for Windoze!

The Your Freedom website did say that I'd need to know how to install a java package.  And I don't!  Can anyone help me?

---

### Post by kpkeerthi on 2008-08-13
Looking at the contents, it seems to be Java app but written for windows. But the usual way to launch a jar file in java would be
```
java -jar <path-to-the-jar-file>.jar
```

---

### Post by ThrobbingBrain66 on 2008-08-13
```
java -jar freedom.jar
```

will do the job I believe.

---

