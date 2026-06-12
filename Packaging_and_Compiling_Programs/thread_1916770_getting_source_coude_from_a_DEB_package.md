---
title: "getting source coude from a DEB package?"
date: 2012-01-28
forum: Packaging and Compiling Programs
---

### Post by shevin on 2012-01-28
Hi I want source code for a program which is no longer avaialbe for developement (bouml) but I have the DEB 

I wonder if we can have the source code for it ?

or do you know any other open source program  that draws Diagrams for classes in a code?

---

### Post by iponeverything on 2012-01-28
maybe dia?

[http://www.addictivetips.com/ubuntu-linux-tips/visio-for-ubuntu-linux-dia-diagram-editor/](http://www.addictivetips.com/ubuntu-linux-tips/visio-for-ubuntu-linux-dia-diagram-editor/)

---

### Post by SevenMachines on 2012-01-29
For UML have a look at Umbrello in the repositories and [argouml]("http://argouml.tigris.org/"), which isnt but is good, and also can be plugged into eclipse

---

### Post by MadCow108 on 2012-01-29
its still in ubuntu, so *apt-get source bouml* will get you the source code

---

### Post by haqking on 2012-01-29
you can use file-roller to extract a specific file from the .deb package.

just browse the deb with archive manager or whatever and extract whatever you want from it

---

### Post by Bachstelze on 2012-01-29
> **haqking said:**
> you can use file-roller to extract a specific file from the .deb package.

just browse the deb with archive manager or whatever and extract whatever you want from it

That won't help, though, because the source code is generally not in a binary deb.

---

### Post by shevin on 2012-01-30
> **MadCow108 said:**
> its still in ubuntu, so *apt-get source bouml* will get you the source code

thanks I did that command , but I dont know where exactly it stored the source code ?

---

### Post by MadCow108 on 2012-01-30
it tells you while running.
its *sourcepackagename-version*
the sourcepackage name can be queried with e.g. apt-cache show package | grep Source

---

