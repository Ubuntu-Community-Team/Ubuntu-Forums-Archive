---
title: "Cannot find Java. Please use --jdkhome to switch the jdk path"
date: 2014-08-07
forum: Programming Talk
---

### Post by dylan0005 on 2014-08-07
Hello everyone!

This error shows up when I try to run **Netbeans (OS independent Zip)** and I have no idea what could be the problem. I do have installed java jdk 7 in my computer but this path : 
                                              netbeans_jdkhome="/usr/lib/jvm/java-7-openjdk-i386"    

This path doesn't work, I mean "*java-7-openjdk-i386*"  is the folder where is located. So, Wheter I'm writing the wrong path or I have to add something to it I need your help!! **How can I do to make it work?**   [SIZE=1] *PD: I'm using lubuntu 14.04*[/SIZE]

---

### Post by ofnuts on 2014-08-08
This [NetBeans wiki]("http://wiki.netbeans.org/FaqJdkHome") hints that that netbeans_ jdkhome should point somewhere in /usr/bin rather thant in /usr/lib.

---

### Post by dylan0005 on 2014-08-08
Thank you *ofnuts* but unfortunately *usr/bin* also doesn't work, at least, when you say "it should point somewhere" inside the folder *bin*, so what archive should I put? I tried with *usr/bin/java* to fix it, however, as I mentioned it doesn't worked too! 
I thing my problem is I am putting the wrong path because I don't know if I should put the whole folder where java jdk is located or directly to the archive...
In conclusion, Can you help me to write the correct path to jdk?

---

### Post by ofnuts on 2014-08-09
Do you have a directory /usr/lib/jvm/java-7-openjdk-i386? If so do you have a /usr/lib/jvm/java-7-openjdk-i386/bin/javac?

By the way are you really meaning to use the 32-bit version? Normally you have a /usr/lib/jvm/default-java which should be a link to the JDK to use.

---

### Post by dwhitney67 on 2014-08-10
> **ofnuts said:**
> This [NetBeans wiki]("http://wiki.netbeans.org/FaqJdkHome") hints that that netbeans_ jdkhome should point somewhere in /usr/bin rather thant in /usr/lib.

I have never seen, nor had, this issue.  Perhaps it was because I had JAVA_HOME defined to the location where I had my Java JDK installed.

Note, under Linux systems, the JDK package can be installed anywhere one wishes to install it.

P.S.  I also define JDK_HOME to be the same as my JAVA_HOME; it's probably redundant, but some scripts I run use one or the other.

---

### Post by dylan0005 on 2014-08-10
I just wrote the path like this:* usr/lib/jvm/java-7-openjdk-i386/jre*  and **netbeans** loaded(very slow but it loaded), nevertheless, another problem just came out, some modules can't load. Would it be the same problem? I hope no...

P.D. I tried* usr/lib/jvm/defalut-java *also and the same situations with modules.

---

### Post by dwhitney67 on 2014-08-10
> **dylan0005 said:**
> I just wrote the path like this:* usr/lib/jvm/java-7-openjdk-i386/jre*  and **netbeans** loaded(very slow but it loaded), nevertheless, another problem just came out, some modules can't load. Would it be the same problem? I hope no...

Probably not.  Just open another thread.

P.S.  Have you tried to build your project without the need of an IDE?  It would not hurt you to learn how the silly IDE does things.

---

### Post by dylan0005 on 2014-08-10
mmm.. not yet. How's it work?

It shows me "_netbeans runs without JDK, just with JRE_" and It asks me for the location of JDK. I don't know what else to do with that path...

---

### Post by dwhitney67 on 2014-08-11
Netbeans runs with a JRE, however if you want to develop Java applications, then eventually you will need to compile them with a JDK.

---

### Post by dylan0005 on 2014-08-11
I see... I just need that netbeans can recognize and find JDK.. the question is: Which could it be the correct path? I'm frustrated, nothing works

---

### Post by dwhitney67 on 2014-08-11
Let's start from step 1... how did you install OpenJDK on your system?  Did you perform a manual installation, or did you rely on the Ubuntu Software Manager?

Second, which version of Netbeans are you attempting to use?  I just download version 8.0 onto my Kubuntu 14.04 system, and it automatically detects the latest version of the JDK I have installed on my system.

Note:  For professional reasons, I am obliged to use Oracle (previously Sun) JDKs for Java development, hence I have these installed on my system.  I do not use OpenJDK.

---

