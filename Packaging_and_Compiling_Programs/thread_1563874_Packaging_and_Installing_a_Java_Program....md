---
title: "Packaging and Installing a Java Program..."
date: 2010-08-29
forum: Packaging and Compiling Programs
---

### Post by KdotJ on 2010-08-29
Ok so, I have made my Java program and now ready to package it into a deb file. My question is how should I have it setup itself on a guest system? Now I know that Java is not the best for Ubuntu, and can't be compiled into bytecode that doesn't require the JVM firing up. So how should I go about this?

This is my guess so far...

- I package the Java program into a .JAR file 
- Build my DEB file
- Have the DEB file install this JAR file into a folder in **/opt**
- Have the DEB file install an executable bash script in **/usr/local/bin** which contains the code to run the JAR file.

e.g.
```

#!/bin/bash
java -jar /opt/packagename/filename.jar

```


Is this method OK? I know it works as I have already tested it out. But is there a better method? I can't compile it all to one file in /usr/local/bin like other programs can I?

Any help is greatly appreciated

---

### Post by SevenMachines on 2010-08-31
Java's fine for linux these days now theres openjdk (the default-jre).
Short answer is, use javahelper, it'll make your life easier

Basically, 
* All you need is your source .java files and then....
* Have a look at [debian wiki]("http://wiki.debian.org/Java/Packaging"), [tutorial]("http://pkg-java.alioth.debian.org/docs/tutorial.html") and [examples]("http://pkg-java.alioth.debian.org/examples/") entries. In particular the [program with a library dependency example]("http://pkg-java.alioth.debian.org/examples/program/"). 

This shows an example entire debian directory for an example java program, foo, with a dependency on a library libtrove-java. Essentially debhelper,
* Builds a jar file from the source
* installs the source to the right place (/usr/share/foo/foo.jar)
* link the jar to /usr/bin/foo and make it executable

You'll probably find that one of the examples linked to above can be used for your own program with minimal changes

---

### Post by KdotJ on 2010-08-31
Thank you so much for those links! That's just what I was after. After having a look through them links, I am also looking up about using Ant to automate the build process before packaging as javahelper can use the Ant files. Does anyone help use this approach too?

Thanks again

---

### Post by KdotJ on 2010-08-31
Ok so I read over all of the examples and tutorials, and built a few debs with java projects. No luck.. I managed to get to the point where the debs install ok, but nothing is actually installed to the computer... apart from the package entry. Hmmm

---

### Post by SevenMachines on 2010-08-31
if you can upload any code/logs? I take it you have no problem when you debuild the examples above?  If the jar is building ok but not being installed, you might want to check your debian/<package>.install file

---

### Post by KdotJ on 2010-09-01
> **SevenMachines said:**
> if you can upload any code/logs? I take it you have no problem when you debuild the examples above?  If the jar is building ok but not being installed, you might want to check your debian/<package>.install file

Hey thanks for the reply,
I had trouble building the debs in the examples, the control file was missing some elements and contained some "user-defined" elements too. I am using 

```
dpkg --build <package name>
```

To build the debs, I also had to change the 'debian' directory to 'DEBIAN' for it to build. 
Is there a difference as the example is for Debian? Are the deb packages on ubuntu slightly different? My .install file is correct to that of the examples... But maybe as I edited the files in the DEBIAN folder to get it to build, I messed something up??

I'll post some code when I have access to my laptop though,
But when I install my deb with the GUI application, the terminal output just says unpacking and setting up. And it only takes a second...

 thanks for your help

---

### Post by SevenMachines on 2010-09-01
$ dpkg --build 
is the wrong command. it builds a deb file out of a filesystem heirarchy. debian directories are lower case for packaging, upper case in the final built deb package, they shouldnt be changed. you should use

$ debuild

or 
$ debuild -b -us -uc 

if you just want to build a deb package and dont want to sign it and deal with all that

---

### Post by KdotJ on 2010-09-01
> **SevenMachines said:**
> $ dpkg --build 
is the wrong command. it builds a deb file out of a filesystem heirarchy. debian directories are lower case for packaging, upper case in the final built deb package, they shouldnt be changed. you should use

$ debuild

or 
$ debuild -b -us -uc 

if you just want to build a deb package and dont want to sign it and deal with all that

Abu right I thought something was up seeing as I had to change so much stuff. Thank you so much, I'll report back once I'm back at my laptop and gave it a shot

---

### Post by KdotJ on 2010-09-01
Update:

Well it took a little bit of googling as I got stuck with the orig.tar.gz business. Nonetheless I managed a successful deb build and tested it all for install after. It works perfectly... Thank you

---

