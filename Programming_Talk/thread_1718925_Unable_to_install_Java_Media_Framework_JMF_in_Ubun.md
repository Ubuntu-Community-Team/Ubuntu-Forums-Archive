---
title: "Unable to install Java Media Framework JMF in Ubuntu 10.04"
date: 2011-04-01
forum: Programming Talk
---

### Post by pongsate1 on 2011-04-01
I'm doing the project to create a video conference application in Java. I do some research and found that JMF is useful.

However, after 2 days of googling, I still cannot install JMF to my Ubuntu 10.04.

I obtain .bin from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter"). Follow the instructions from [https://bugs.edge.launchpad.net/ubuntu/+bug/104511]("https://bugs.edge.launchpad.net/ubuntu/+bug/104511"). Use the command from [http://www.linuxquestions.org/questions/programming-9/explain-an-instructions-212224/]("http://www.linuxquestions.org/questions/programming-9/explain-an-instructions-212224/"). But I still cannot pass the diagnostics [http://www.oracle.com/technetwork/java/javase/jmfdiagnostics-139189.html]("http://www.oracle.com/technetwork/java/javase/jmfdiagnostics-139189.html"). I don't know what to do anymore. 

Please help...

---

### Post by pongsate1 on 2011-04-01
This is the code that obtained from diagnostics error's detail


load: class JMFDiagnostics not found.
java.lang.ClassNotFoundException: JMFDiagnostics
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadClass0(Plugin2ClassLoader.java:250)
	at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Plugin2ClassLoader.java:180)
	at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Plugin2ClassLoader.java:161)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:687)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:3025)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1498)
	at java.lang.Thread.run(Thread.java:662)
Exception: java.lang.ClassNotFoundException: JMFDiagnostics

---

