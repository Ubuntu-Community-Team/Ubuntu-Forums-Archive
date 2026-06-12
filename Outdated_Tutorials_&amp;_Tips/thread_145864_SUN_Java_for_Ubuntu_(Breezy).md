---
title: "SUN Java for Ubuntu (Breezy)"
date: 2006-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by knalle on 2006-03-17
This guide is made for those who explicitly wants to run SUN Microsystems' JDK/JRE. For anybody else there are good Java support in the official Java repositories.

To run the SUN JDK or JRE you need to satisfy some system dependencies and enable “multiverse”, if you don't know what this means or object to **multiverse** this guide is not for you. First enable enable **multiverse**:
```
sudo gedit /etc/apt/sources.list
```
after each occurrence of the word **universe** add the word **multiverse**. Save the file and exit your editor, then refresh the repositories;
```
sudo apt-get update
```
Now install the dependencies:
```
sudo apt-get install fakeroot java-package java-common
```
Goto Sun's website [http://java.sun.com/](http://java.sun.com/) and download the Linux .BIN version of Java JDK or JRE that you want. The rest of this guide uses J2jsdk-1.4.2 but you can use any Linux JDK/JRE from SUN's website. Download the .BIN file to some place and create the .DEB file:
```
fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i386.bin
```
install newly created .DEB file:
```
sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb
```
Now make SUN's Java the default by running this command and selecting it.
```
sudo update-alternatives --config java
```
you can now check your Java with:
```
java -version
```
if you have the JDK you can now also use the compiler:
```
javac
```
Happy Hacking!

---

