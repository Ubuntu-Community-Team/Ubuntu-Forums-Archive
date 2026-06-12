---
title: "Unable to find JVM?!"
date: 2007-03-31
forum: Programming Talk
---

### Post by samjh on 2007-03-31
I've recently uninstalled sun-java5 and installed sun-java6 from the backports repository.

The problem is I cannot run binary executables that are supposed to launch the JVM.  For example, I cannot run Eclipse using the binary launcher, because this error comes up:
```

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/username/eclipse/jre/bin/java
'java' in your current PATH
```

[EDIT]

Solution found.  Symlinks to java need to be created in usr/bin.

---

### Post by smokey edgy on 2007-04-01
> Samjh:

Does java run when you attempt to launch it in the command line?

Did you change your JAVA_HOME in /home/jhaln/.eclipse/eclipserc? It might work if your eclipserc has something like:

```

JAVA_HOME=/usr/lib/jvm/java-6-sun/

```

---

### Post by pinche on 2007-04-04
I didn't have an eclipserc file in my ~/.eclipse.  Created it, added JAVA_HOME var, exported it, and ran "source ~/.eclipse/eclipserc" and everything works perfectly.  Thanks!

---

### Post by lucabk on 2007-04-12
I'm sorry i'm a "ubuntu newbie"... 

"Symlinks to java need to be created in usr/bin"

Do you mean something like

ln -s /home/myuser/java1.6 /usr/bin/java ??

Thanks.

---

### Post by samjh on 2007-04-12
Yes, Lucabk.

---

### Post by chimiasanchi on 2008-05-06
on my fresh Hardy Heron install, I had a problem with running eclipse after installing it with synaptic (and with the (Add/Remove... tool in the main panel menu). I got the error  

```
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.6-sun...not found
  testing /usr/lib/j2sdk1.5-sun...not found
  testing /usr/lib/j2sdk1.4-sun...not found
```

an error window popped up saying: 
```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java
```

so i went searching for the java virtual machine that was installed by default. i found it in the directory /usr/lib/jvm/java-6-openjdk

so this command 

echo 'JAVA_HOME=/usr/lib/jvm/java-6-openjdk' > ~/.eclipse/eclipserc 

created the necessary configuration file, and eclipse starts, but gives me the following complaint:

```
using specified vm: /usr/lib/jvm/java-6-openjdk
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

```

so just run these commands: 

```
sudo touch /usr/local/lib/eclipse/.eclipseextension
sudo chmod 2775 /usr/local/lib/eclipse/.eclipseextension
sudo chown root:staff /usr/local/lib/eclipse/.eclipseextension


```

it's running now. i've never used eclipse before, but i'm anxious to check out eclipse-pydev

---

### Post by revchris on 2008-05-08
I still can't get it to run:

[INDENT]A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java[/INDENT]

I don't even have /usr/lib/j2sdk1.4-sun/bin/java.  I'm using OpenJDK, so it should be looking in /usr/lib/jvm.

---

