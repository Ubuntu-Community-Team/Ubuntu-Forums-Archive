---
title: "anyone have the java web services pack on ubuntu?"
date: 2009-03-17
forum: Programming Talk
---

### Post by badperson on 2009-03-17
I tried running the .sh file and got this:

```
For help, type 'jwsdp-2_0-unix.sh -help'
 
Using /var/tmp as temporary directory...
Searching for Java(TM) 2 Platform, Standard Edition...
tail: cannot open `+368' for reading: No such file or directory
Initializing InstallShield Wizard...
Exception in thread "main" java.lang.NoClassDefFoundError: JWSDP
Caused by: java.lang.ClassNotFoundException: JWSDP
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: JWSDP. Program will exit.

```

does it need to be in a particular directory?

---

### Post by duedl0r on 2009-04-08
```

tail --bytes=+368 ./jwsdp-2_0-unix.sh > jwsdp.jar
unzip jwsdp.jar
java JWSDP

```

did it for me

---

### Post by badperson on 2009-04-08
thanks, 
I tried that and got this error:

```
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)

```
bp

---

### Post by aguizar on 2011-09-03
> **badperson said:**
> thanks, 
I tried that and got this error:
The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
If you run the jwsdp install script as shown below.
```
sh jwsdp-2_0-unix.sh -is:debug 1
```it will print the reason why it fails. In my case the output is:
```
com.jxml.quick.QPE; lineNumber: 0; columnNumber: 0;  java.lang.ClassNotFoundException:  sun.beans.editors.BoolEditor
```followed by a stack trace.

In my computer, the install script is detecting and using OpenJDK 6 to  run the JWSDP installer. Unfortunately it seems to rely on this  sun.beans.editors.BoolEditor class which is not part of the Java API.  The rt.jar shipped with OpenJDK 6 includes  sun.beans.editors.BooleanEditor but not BoolEditor.

My solution was to tell the installer to use Sun JDK 5 to run the JWSDP installer, as follows.
```
sh jwsdp-2_0-unix.sh -is:javahome /etc/alternatives/jre_1.5.0
```If needed, replace **/etc/alternatives/jre_1.5.0** with your Sun JDK 5 home directory.

---

