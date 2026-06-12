---
title: "What is The Deference between Java 5 and Java6"
date: 2010-04-25
forum: Programming Talk
---

### Post by Uchiha_madara on 2010-04-25
What is the Major Defference Between those 
Two Versions of Java.....

---

### Post by GregBrannon on 2010-04-25
Wikipedia has a nice summary at the page "Java Version History."

---

### Post by kavon89 on 2010-04-25
If you're working with Swing, JDK 5 doesn't support SwingWorker, SystemTray, and I think SwingUtilities.

---

### Post by Uchiha_madara on 2010-04-26
> If you're working with Swing, JDK 5 doesn't support SwingWorker, SystemTray, and I think SwingUtilities.



Are you sure ..???

I remember that i have worked with JDK 5 or 1.5 I was Import Swing and work with it ...

> 

import javax.swing.*;

//
//Complement of the Code .....
//



What are the Enhancments done on JDK 1.6 that make it special ?

---

### Post by kavon89 on 2010-04-26
[SwingWorker]("http://java.sun.com/javase/6/docs/api/javax/swing/SwingWorker.html") and [SystemTray]("http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html") are new in 1.6, part of the GUI and Swing improvements. It's really easy to backport SwingWorker for 1.5 in your projects but I don't think you can do this with SystemTray, which honestly has a pretty crappy implementation right now (so a 3rd party library is probably a better choice for this).

A summary of the rest of the enhancements that Java 6 offers is listed [here]("http://en.wikipedia.org/wiki/Java_version_history#Java_SE_6_.28December_11.2C_2006.29").

---

