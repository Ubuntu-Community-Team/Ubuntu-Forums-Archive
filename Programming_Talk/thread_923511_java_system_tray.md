---
title: "java system tray"
date: 2008-09-18
forum: Programming Talk
---

### Post by Geir102 on 2008-09-18
Hi I'm writing some software in java6SE. Im using the systemtray. It workes on my other ubuntu box but not on this one:( The program works fine except the systemtray. Limewire shows up whit systemtray thats java to. Any one know whats can be wrong?

---

### Post by jespdj on 2008-09-18
Can you show us your code?

---

### Post by xlinuks on 2008-09-18
The (native) system tray in Java 6 doesn't work when you have 3D enabled (like compiz), however this has been fixed in Java 6 update 10 which is only a release candidate so far. I would suggest being more specific on the issue like jespdj mentioned.

---

### Post by Geir102 on 2008-09-18
The code isent really mine to give.
But if you look at the exsample form [http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)
Its the same thing. running the code gives "System tray is currently not supported." Im not running and 3D its a normal GUI program. It's rally strange.

---

### Post by drubin on 2008-09-18
You could try a bit of a native aproche I used in JDK<1.6
[https://jdic.dev.java.net/documentation/incubator/tray/](https://jdic.dev.java.net/documentation/incubator/tray/)

---

### Post by tinny on 2008-09-18
> **Geir102 said:**
> ( The program works fine except the systemtray. Limewire shows up whit systemtray thats java to. Any one know whats can be wrong?

Limewire has had this functionality before Java 6, right? So limewire does not use Java 6 for the system tray functionality. The JDIC (Java Desktop Integration Components) project that rubinboy has pointed out is very popular, so I wouldn't be surprised if limewire uses that.

If you use JDIC you will gain Java 5 level compatibility too. :-)

---

### Post by Geir102 on 2008-09-26
nice tanks I'll try that

---

