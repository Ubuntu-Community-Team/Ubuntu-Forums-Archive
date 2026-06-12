---
title: "Creating a jar file from eclipse with mysql driver"
date: 2007-04-23
forum: Programming Talk
---

### Post by th3james on 2007-04-23
Hi

For my computer science course i am writing a java program that connects to a mysql database on my local machine. I downloaded the mysql jdbc driver from the mysql website, and added mysql-connector-java-5.0.5-bin.jar to the java build path libraries in eclipse (Project -> Properties -> Java build path). The program runs and connects to the database in eclipse, but when i try to run the jar file i created from the project, when connecting to the database i get this error:

```
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at CustomerForm.getResults(CustomerForm.java:125)
        at CustomerForm.layout(CustomerForm.java:53)
        at CustomerForm.<init>(CustomerForm.java:115)
        at mainForm.actionPerformed(mainForm.java:83)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3260)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
SQLException: No suitable driver found for jdbc:mysql://localhost/garits
```

I've tried playing around with java at CLI with the -classpath option, but im finding the tutorials online a bit confusing, is there anyway i can get eclipse to export it and just make it work?

any help/nudges in the right direction HUGELY appreciated

thanx
James

---

### Post by rjfioravanti on 2007-04-23
Hi I think you have to create your .jar file with a special manifest file

This manifest file gives you instructions on which class the main is located in, and classpath options

The following URL shows how to setup a manifest file before exporting a JAR in a SQL Anywhere project, but Eclipse is Eclipse and it doesn't matter

Instructions you want start on page 8 

[http://www.ianywhere.com/downloads/whitepapers/creating_database_app_with_SA_and_Eclipse.pdf](http://www.ianywhere.com/downloads/whitepapers/creating_database_app_with_SA_and_Eclipse.pdf)

---

### Post by phossal on 2007-04-23
Here is a link to a thread about [JDBC and MySQL]("http://ubuntuforums.org/showthread.php?t=409640"). I wrote a very simple class to connect to MySQL from Java using the MySQL jar for the OP. Depending on how widely you're going to distribute your program, the simplest solution may be to drop the .jar file into the <path_to_jre>/lib/ext folder. You can do that on any machine and your program will work.

---

### Post by th3james on 2007-04-24
I was able to get it working using phossal's method, i was unable to get the special manifest file to work, i just got the same error, which is a shame because it was a slightly more elegant solution for redistribution, but oh well
Thanks guys!

---

