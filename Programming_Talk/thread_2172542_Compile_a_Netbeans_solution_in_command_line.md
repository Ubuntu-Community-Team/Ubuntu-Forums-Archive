---
title: "Compile a Netbeans solution in command line"
date: 2013-09-05
forum: Programming Talk
---

### Post by raac on 2013-09-05
Hi guys, making a program run using IDE is so simple, but I really want to know how to do it from the command line. So the way the project is structure is as follows

ProjectName -> src (package) -> Objects (package)
ProjectName -> src (package) -> purchasereceiver (package)

I have 4 classes one is in the "Objects" package and the other three are in "purchasereceiver" package

In the solution I added the JDBC jar files into the project libraries. the jar file is located under ~/Documents/jarFiles/

It runs just fine in NetBeans

So, I wanted to switch to the command line. First of all what should the global CLASSPATH be? Should it be the directories where I have my *.java files and *.jar files? If that's the case, would I need to update it every time I created a new project. If I create a new project there will be a new *.java files in new directories, so are those directories need to be added in the CLASSPATH??

Anyway, since I wasn't sure I decided to add the classpath as a parameter. Should I do it a compile time or when I run it or both??

I.e.

javac -cp //something

or

java -cp //something

So far what I have done is the following..

javac -cp */home/tony/Documents/Projectname/src/Objects/*:*/home/tony/Documents/Projectname/src/purchasereceiver/*:*/home/tony/Documents/jarFiles/* **/home/tony/Documents/Projectname/src/Objects/*.java /home/tony/Documents/Projectname/src/purchasereceiver/*.java**

I then execute the following line

java -cp *//same as above* **/home/tony/Documents/Projectname/src/PurchaseReceiver/PurchaseReceiver**

NOTE:PurchaseReceiver.java is class that has the main method.

The result is the following
Exception in thread "main" java.lang.NoClassDefFoundError: PurchaseReceiver (wrong name: purchasereceiver/PurchaseReceiver)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:788)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:447)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:71)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:361)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
        at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)

[B]
Your help would be very appreciated.

Thanks.


[/B]

---

### Post by raac on 2013-09-05
Clearly there is something that I'm doing wrong. I moved all the *.java files and *.jar files from the project into the same directory. It compiles fine, and then, from the directory, I ran it like this

java -cp . PurchaseReceiver, and it throws the same error.

I looked online and the class path should be wherever the .class and .jar files are located. That's what I did with the "." 

Maybe I made a mistake on something else.

---

