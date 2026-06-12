---
title: "Android Emulator"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-11-09
I have downloaded the Android emulator of Google's site and there is a file in it called android.jar that I'm guessing I am supposed to run. How do I run it?

---

### Post by phidia on 2008-11-09
Do you have a java run environment installed? Open a terminal and enter > java -version

If you have the jre you should be able to double click or right click the file to run it. Did a README file come with the download?

---

### Post by RadiationHazard on 2008-11-09
This is what happened.

```
jordan@jordan-laptop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)
jordan@jordan-laptop:~$ 

```

---

### Post by OutOfReach on 2008-11-09
In the android directory, there should be a directory called 'tools', switch into that directory and then start the executable named 'emulator'. :)
If nothing appears to happen, goto into a terminal and launch it from there to see if you get any useful information.

---

