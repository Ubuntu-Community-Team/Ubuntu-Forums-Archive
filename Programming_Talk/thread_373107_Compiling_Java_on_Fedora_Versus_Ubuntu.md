---
title: "Compiling Java on Fedora Versus Ubuntu ?"
date: 2007-02-28
forum: Programming Talk
---

### Post by elmerfud on 2007-02-28
I recently switched my development computer from fc6 to Edgy.  Everything works great except I can't build certain java applications.

For example, I need to build a new library for libusbJava.
[http://inf.ntb.ch/infoportal/help/index.jsp?topic=/ch.ntb.infoportal/projects.html#libusbjava_installDevice](http://inf.ntb.ch/infoportal/help/index.jsp?topic=/ch.ntb.infoportal/projects.html#libusbjava_installDevice)

On my fc6 box, I download the source ( [https://svn.ntb.ch/svninf/ch.ntb.usb/](https://svn.ntb.ch/svninf/ch.ntb.usb/) ) cd into the directory and do a "ant linux".  It builds without errors.

On edgy, I have installed jdk 5.0 from the ubuntu repositories.  I have deleted the stock Java included with edgy.  I have installed Eclipse and it runs fine.

However, when I run 'ant linux' for libusbJava I get 

"[exec] LibusbJava.cpp:11:17: error: jni.h: No such file or directory"

After much investigation, I compared the synaptic entries for 'java' on both machines.  I found that fc6 is using gcc-java whereas edgy is using gcj.  I don't see gcc-java in the available package list.  

How do I get my application to compile ?    Am I right that jni is obtained from gcc-java ?

 Thanks.

---

### Post by elmerfud on 2007-02-28
On fc6:
$ javac -version
Eclipse Java Compiler v_686_R32x, 3.2.2 release, Copyright IBM Corp 2000, 2006. All rights reserved.

On Ubuntu:
$ javac -version
javac 1.5.0_08

---

### Post by kaamos on 2007-02-28
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=jni.h&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=jni.h&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

java-gcj-compat-dev would be my guess.

---

### Post by elmerfud on 2007-03-01
You are right.  That solved the problem.  It compiled and it runs.

---

