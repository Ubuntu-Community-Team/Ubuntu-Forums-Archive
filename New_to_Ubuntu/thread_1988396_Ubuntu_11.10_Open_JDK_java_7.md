---
title: "Ubuntu 11.10 Open JDK java 7"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by vagelism on 2012-05-27
Hello to all.
When I try from the software center to install Opend JDK  java 7 I always got also the jdk 6!!!
Is it normal? When I right click to a jar file to open with jdk 6 it doesnt do anything but when I choose jdk 7 it works...

Also when I try to run it in the terminal with java -jar ...
I got the message below```
unknown@unknown-pc:~$ java -jar "/home/unknown/NetBeansProjects/ProtocolProject/GeorgeApp/dist/GeorgeApp.jar"
Exception in thread "main" java.lang.UnsupportedClassVersionError: georgeapp/GeorgeApp : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: georgeapp.GeorgeApp. Program will exit.
unknown@unknown-pc:~$ ^C

```

Why all this mess? I am confused!
Thank you!

---

### Post by jtarin on 2012-05-27
JDK java 7 and 6 are both available to download. That's not confusing. If you have both installed you can uninstall one if you wish.
How can I tell what version of Java is installed? You can find this by running a command in a Command Prompt window."java -version"

> Do I need older versions of Java?
The latest available version is compatible with the older versions. However, some Java applications (or applets) can indicate that they are dependent on a particular version, and may not run if you do not have that version installed. If an application or web page you access requires an older version of Java, you should report this to the provider/developer and request that they update the application to be compatible with all Java versions.


---

### Post by vagelism on 2012-05-27
Well when I try to uninstall the 6 vertion then also the 7 dissapear!

---

### Post by jtarin on 2012-05-28
So uninstall them both then go [here ]("http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/")for instructions on installing 7.

Sometimes applications that use Java call for a certain version.....like 6. if this is the case then you are stuck using that version until your software updates. It's OK and not unusual to have two or more versions of Java. 

Try to get out of the habit of using the software center all the time. Learn to use the command line and Synaptic package manager. These will give you a better understanding of how software is installed and relationships between installed software.

---

