---
title: "Eclipse can't find a Java Virtual Machine"
date: 2007-02-22
forum: Programming Talk
---

### Post by matemargo on 2007-02-22
That's the problem.
I have installed j2re from Synaptic, but it was the 1.4 version.
So, I've installed Automatix2 and with it installed Java 6.

If in the terminal I run **java -version** i get:

```

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

But, whe I run Eclipse, I get:

```

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found

```

And an error alerts appers saying:

```

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

```

PS: I have Eclipse 3.2.1

---

### Post by phossal on 2007-02-22
Maybe try:
```
sudo update-alternatives --config java
```
If the correct Java is already installed, perhaps set a JAVA_HOME environment variable and add it to the path.
You can also edit the list of JVM's eclipse checks on startup, depending on how eclipse was installed.

The *methods* are many.

How did you install eclipse?

[EDIT] If you have a valid, functioning *JDK (not JRE)*, you can simply *download* the current eclipse and *extract* the .tar.gz file to your desktop. It's just that easy.

---

### Post by bcursor on 2007-02-23
That works for me.

```
gksudo gedit /etc/eclipse/java_home
```

then add this line to the top of the list

```
/usr/lib/jvm/java-6-sun-1.6.0.00/jre
```

---

### Post by phossal on 2007-02-23
> **phossal said:**
> You can also edit the list of JVM's eclipse checks on startup, depending on how eclipse was installed. The *methods* are many.

Right. The methods are many. But doing it the way you did, bcursor, is dependent on the way you installed eclipse. That file you're referring to is created by the packaged version.

---

### Post by matemargo on 2007-02-24
I have finally solved this downloading Eclipse from the site and point it to my J2re.

Thanks for your reply. :)

---

### Post by spork135 on 2007-04-07
bcursor, I love you and will have your children. I knew its path was wrong but didnt know where to go to edit it. You rule.

---

### Post by phossal on 2007-04-08
> **spork135 said:**
> bcursor,** I love you and will have your children. **I knew its path was wrong but didnt know where to go to edit it. You rule.

What?!  :)

---

### Post by jsidgman on 2007-04-10
I have tried what you have suggested here but eclipse keeps looking at the original information in the /etc/eclipse/java_home file. I have even tried placing the line in my ~.eclipse/eclipserc file but that does not work either.

Any other suggestions?

---

### Post by phossal on 2007-04-10
The easiest, most straight-forward way to install Java's JDK and eclipse is to grab them both from their respective sites. The moderators and the Ubuntu'nuts stress the package installation, but neither Java nor Eclipse is best installed that way. The packages are simply extra layers of abstraction that commonly cause the types of problems you're having, prevent easy updates (when eclipse.org or SUN release them), etc.

Consider the time you've already invested. Just grab them from their sources.

---

### Post by charlieg on 2007-08-15
> **jsidgman said:**
> I have tried what you have suggested here but eclipse keeps looking at the original information in the /etc/eclipse/java_home file. I have even tried placing the line in my ~.eclipse/eclipserc file but that does not work either.

Any other suggestions?
The previous suggestion was slightly wrong.  You don't want the trailing '/jre' and you want to add the generic symbollic link to java6 rather than the specific link (which may change with updates).
```
sudo echo "/usr/lib/jvm/sun-6-java" >> /etc/eclipse/java_home
```
WORKSFORME ;)

---

### Post by mschering on 2007-08-23
This all didn't work for me. This worked:

In the Eclipse directory:

ln -s /usr/lib/jvm/java-6-sun jre

---

### Post by matemargo on 2007-08-23
You can also go to:

**Window/Preferences/Java/Installed JRE's**

There you can search and choose the one you want.

---

### Post by saz on 2008-02-12
```
sa@Thorn:~$ eclipse 
searching for compatible vm...
  testing /usr/lib/jvm/java-6-sun-1.6.0.00/jre...not found
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/core/launcher/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
```

someone can save me?

---

### Post by chimiasanchi on 2008-05-06
there are some more solutions here:

[http://ubuntuforums.org/showthread.php?p=4899635#post4899635](http://ubuntuforums.org/showthread.php?p=4899635#post4899635)

---

