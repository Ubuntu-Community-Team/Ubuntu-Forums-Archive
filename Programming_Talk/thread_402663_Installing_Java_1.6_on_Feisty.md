---
title: "Installing Java 1.6 on Feisty"
date: 2007-04-06
forum: Programming Talk
---

### Post by slf_texas on 2007-04-06
I installed Ubuntu Feisty on my laptop a few days ago to learn Java.  (So much for the common theory that linux is not ready for prime time desktop. I love it.  I suspect it will become my primary desktop environment as I become more familiar with it.  But, ya'll know that and I digress.)

I used the Synaptic Package Manager to install all the Java6 packages and things seems to have gone as expected.  Says the install was successful.  I then went to Sun's Java Tutorial and, starting from the beginning, copied the Hello World program and saved it.  I compiled it using javac and things still appeared to be ok.  When I try to run the program though I get the following error:

Exception in thread "main" java.lang.ClassFormatError: HelloWorldApp (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)[/COLOR]

I'm sure I've missed something in the installation, probably something really simple.  Can anyone be of assistance to a linux amateur? :confused:

---

### Post by no1wantdthisname on 2007-04-06
Looks like you're not using sun's java.  You're using gcj.
```

sudo update-java-alternatives -l
sudo update-java-alternatives -s java-6-sun

```

---

### Post by slf_texas on 2007-04-06
That was the problem.  Don't know exactly what that did, but it worked.  Thank you!!!

Life is good!

---

### Post by samjh on 2007-04-06
> **slf_texas said:**
> That was the problem.  Don't know exactly what that did, but it worked.  Thank you!!!

Life is good!

Ubuntu comes installed with GCJ by default (GCJ is GNU's free implementation of Java).  But in order to have full compatibility with Java, you need to install Java from Sun.

It seems that you had installed Sun Java, but your environment was still configured to run GCJ.  The first update-java-alternatives command lists all the installed versions of Java recognised by Ubuntu.  The second update-java-alternatives command sets Ubuntu to use java-6-sun, which is Sun's Java version 6.

---

### Post by slf_texas on 2007-04-06
Ah.   Thanks for the information.  Every little bit helps.  My journey to become a Java programmer seems to have begun a considerable distance before the starting line.  Let the adventure begin.

---

### Post by Telengard C64 on 2007-05-08
That was **exactly** what I needed to get Sun Java working on Kubuntu Feisty Fawn 7.04. See this page for the gory details of my ordeal:

[http://www.kubuntuforums.net/index.php?ind=blog&op=home&idu=13553&singlepost=96]("http://www.kubuntuforums.net/index.php?ind=blog&op=home&idu=13553&singlepost=96")

Thank you very much!
:) 

> **no1wantdthisname said:**
> Looks like you're not using sun's java.  You're using gcj.
```

sudo update-java-alternatives -l
sudo update-java-alternatives -s java-6-sun

```

---

### Post by phossal on 2007-05-08
The backports version usually trails at least an update, if not a full version, behind whatever SUN's current release is. I hate the package managers. The package just wraps SUN's .bin file - which makes me wonder why anyone would use it. To each his own.

---

### Post by FaceLeg on 2007-06-04
Really helpful, thanks!

I used the directory it gave me to point Eclipse in the right direction.

---

