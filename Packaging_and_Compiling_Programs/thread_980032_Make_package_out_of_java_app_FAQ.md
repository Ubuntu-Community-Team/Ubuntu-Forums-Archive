---
title: "Make package out of java app FAQ?"
date: 2008-11-12
forum: Packaging and Compiling Programs
---

### Post by gjosef on 2008-11-12
Hi,

Is there a good FAQ or how-to somewhere on how to create debs to install java apps? For someone who knows how to make java apps, but nothing about installing on linux systems (where should the app go, should class files be prepackaged into jar-files, etc, etc).

---

### Post by uljanow on 2008-11-13
It's recommended to put all files in a jar archive. According to Debian policy the jar files should be located in **/usr/share/java** . The deb package should always depend on a meta-package like java6-runtime instead of a particular java package .

---

### Post by gjosef on 2010-08-18
Here is a good article on how to easily build your own deb packages:
[http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/]("http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/")

---

