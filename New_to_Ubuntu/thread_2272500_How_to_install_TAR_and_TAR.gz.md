---
title: "How to install TAR and TAR.gz"
date: 2015-04-07
forum: New to Ubuntu
---

### Post by sebastiaan5 on 2015-04-07
So i downloaded JDK-8u40-linux-x64.tar.gz i can extract it to a folder where i can see all the files but I don't know how to install. Do i need to use a command in terminal?

greetz

---

### Post by slickymaster on 2015-04-07
> **sebastiaan5 said:**
> So i downloaded JDK-8u40-linux-x64.tar.gz i can extract it to a folder where i can see all the files but I don't know how to install. Do i need to use a command in terminal?

greetz
If you want to install Java, I would advise you against doing it that way and to opt for installing it via the Web Upd8 PPA repository. This PPA supports JDK8 for both 32bit and 64bit as well as ARM and everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin.

It's as simple as running these three commands in a terminal window:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by buzzingrobot on 2015-04-07
> **sebastiaan5 said:**
> So i downloaded JDK-8u40-linux-x64.tar.gz i can extract it to a folder where i can see all the files but I don't know how to install. Do i need to use a command in terminal?


Some points to remember:

1. Your Ubuntu system uses a package manager program that maintains a database of every software package installed on it.  The key word here is:  Package.  A 'package' is an archive of software that contains the components of a program as well as instructions the package manager uses to install it automatically and correctly. (There can be hundreds of components in a package.)

2. The package manager also determines any other packages that must be downloaded and installed to support the specific package you're installing.  Those are the 'dependencies'.

3.  The package manager also determines which packages have available updates, then downloads and installs them.

4. Nothing in points 1, 2, or 3 happens when you install software from a tar archive. Tar archives contain whatever the person who created it wanted it to contain.  Traditionally, they've been used for source code. (Tar packages date from the very first days of Unix, when tools like package managers and dependency resolvers did not exist.)

5. Installing from a tar archive means you get to unpack the archive, very likely figure out how to compile the source code inside it, then ensure that all the components are moved to the correct locations in the file system. Then, you get to handle all future updates and patches because the package manager will be unaware that software is on the system.

6.Bottom line:  Use the package manager to install software.  The Software Center, Synaptic, apt-get, etc., are all front ends to the same package manager.

---

