---
title: "Where Is OpenJDK 7 Installation Directory?"
date: 2012-05-02
forum: Programming Talk
---

### Post by digiPixel on 2012-05-02
Been trying to locate where OpenJDK 7 is installed to on Ubuntu 12.04 LTS but have ended up at a dead end. In the previous Ubuntu LTS version one could find out where a package was installed to via Synaptic, in the properties for the selected package.

Does the Ubuntu Software Center have some functionality for finding out where a package has been installed to? Need the information in order to add OpenJDK 7 as a second Java platform for NB 7.1.

I'm not sure if it is possible to change the default JDK used by NB once it has been set during installation.

---

### Post by 11jmb on 2012-05-02
It's probably in /usr/bin

If not, try opening a terminal and type 
```

whereis java

```

see if that helps.

---

### Post by digiPixel on 2012-05-02
> **11jmb said:**
> It's probably in /usr/bin

If not, try opening a terminal and type 
```

whereis java

```

see if that helps.


Not much help I'm afraid. Normally the JDK is installed somewhere in /usr/lib if I recall correctly. NB doesn't recognise the JDK in /usr/share/java when adding a new Java platform.

---

### Post by 11jmb on 2012-05-02
Hmm I won't be much help with netbeans, but I'm pretty sure Ubuntu Software Center will install all of your software in its proper /usr location. you could try a "grep -r -l java /usr" and seeing what comes up. For some weird reason, it may have been installed in /usr/local, as well.

Also, what is your output from "whereis java"?

---

### Post by digiPixel on 2012-05-02
> **11jmb said:**
> Hmm I won't be much help with netbeans, but I'm pretty sure Ubuntu Software Center will install all of your software in its proper /usr location. you could try a "grep -r -l java /usr" and seeing what comes up. For some weird reason, it may have been installed in /usr/local, as well.

Also, what is your output from "whereis java"?

Here is the output from the whereis command:

**java: /usr/bin/java /usr/bin/X11/java /usr/share/java /opt/jdk1.7.0/bin/java /usr/share/man/man1/java.1.gz**


The directory **/opt/jdk1.7.0** I know about since I installed the Oracle JDK to that location.

---

### Post by r-senior on 2012-05-03
On my 64-bit system it is /usr/lib/jvm/java-7-openjdk-amd64.

To find your JDK directory reliably you need to follow the links to your javac executable through the alternatives system until you stop hitting symbolic links

```
$ which javac
/usr/bin/javac
$ ls -l /usr/bin/javac
lrwxrwxrwx 1 root root 23 May  2 10:02 /usr/bin/javac -> /etc/alternatives/javac
$ ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 43 May  2 10:02 /etc/alternatives/javac -> /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
$ ls -l /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
-rwxr-xr-x 1 root root 6352 Apr 13 04:00 /usr/lib/jvm/java-7-openjdk-amd64/bin/javac

```

The location of the JDK for Netbeans, Eclipse, etc. is the directory above the 'bin' directory that contains javac. Hence '/usr/lib/jvm/java-7-openjdk-amd64'.

---

### Post by digiPixel on 2012-05-03
> **r-senior said:**
> On my 64-bit system it is /usr/lib/jvm/java-7-openjdk-amd64.

To find your JDK directory reliably you need to follow the links to your javac executable through the alternatives system until you stop hitting symbolic links

```
$ which javac
/usr/bin/javac
$ ls -l /usr/bin/javac
lrwxrwxrwx 1 root root 23 May  2 10:02 /usr/bin/javac -> /etc/alternatives/javac
$ ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 43 May  2 10:02 /etc/alternatives/javac -> /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
$ ls -l /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
-rwxr-xr-x 1 root root 6352 Apr 13 04:00 /usr/lib/jvm/java-7-openjdk-amd64/bin/javac

```

The location of the JDK for Netbeans, Eclipse, etc. is the directory above the 'bin' directory that contains javac. Hence '/usr/lib/jvm/java-7-openjdk-amd64'.


Found where OpenJDK 1.7 was installed to. OpenJDK is located in the following directory:

[INDENT]**/usr/lib/jvm/java-1.7.0-openjdk-i386**[/INDENT]

NB detected the OpenJDK once it was pointed to where it was installed to. The IDE detected the name and where the docs are located but couldn't locate the sources. Is there a separate OpenJDK 1.7 Sources package that needs to be installed?

---

### Post by digiPixel on 2012-05-03
Ok, adding the new Java platform has resulted in the JavaFX tab appearing. I do wonder if the next NB update will make it unnecessary to add a new Java platform in order to register a new JavaFX platform.

---

