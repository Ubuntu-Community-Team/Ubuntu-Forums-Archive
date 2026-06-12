---
title: "Compiling java"
date: 2006-03-12
forum: Packaging and Compiling Programs
---

### Post by halfway on 2006-03-12
Hey,

I was wondering if there is any java compiler built in to ubuntu or do you have to install it from somewhere (from the cd or the net)? I've tried 'gcj' but it isn't there.

Thanks in advance.

---

### Post by Klejs on 2006-03-12
If you run:

```
apt-cache search java | grep compile
```

It do find some compilers, but then its all up to you to
install and make an opinion.

Have fun!

---

### Post by knalle on 2006-03-12
```
sudo apt-get install gcj-4.0
```

But from religious reasons i only use the Sun SDK for all my compiling

First you will need to add all the extra repositories for Ubuntu. (ie Multiverse, Universe...) Please see other how to's on how to do that.

Now go to Sun's website [http://java.sun.com/](http://java.sun.com/) and select the java jdk or jre that you want.

This example uses J2jsdk-1.4.2 but you can use any J2sdk. Run similar commands from the terminal:

First install the required packages:

```
sudo apt-get install fakeroot java-package java-common
```

Create the Deb file for the install:

```
fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i586.bin
```

Install The deb file

```
sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb
```

Now make Sun's java the default by running this command and selecting it.

```
sudo update-alternatives --config java
```

you can now check your java sdk with:

```
java -version
```

java version "1.4.2_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_10-b03)
Java HotSpot(TM) Client VM (build 1.4.2_10-b03, mixed mode)

Happy Hacking!

---

### Post by halfway on 2006-03-12
Will give that a try when i get home. Thanks.

---

