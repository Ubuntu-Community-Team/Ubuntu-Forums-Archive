---
title: "python - creating debian package for py app"
date: 2009-11-29
forum: Programming Talk
---

### Post by Maverick5x on 2009-11-29
Hello,

I've recently finished creating an application using python.
Now the project contains alot of files and therefore, am unable to find resources about how the files should be structured.

My questions are:
1) where is the main file going to reside in? /usr/bin?
2) What about the directory which will contain the included modules? /usr/lib?
3) data files including sqlite database in /etc/appname?

Thanks in advance
Rakan

---

### Post by nvteighen on 2009-11-29
A Debian package is a .tar.gz that internally resembles the system's data structure + some metadata that regulate installation and other processes. This "fake" system is created in packaging through a series of scripts, specially a Makefile called "rules".

The best guide I've seen for Python is the Ubuntu official one: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

Python has some issues that makes packaging more difficult than C projects' or others'.

---

### Post by oldfred on 2009-11-29
I have not used it but this seems to cover some of your questions:

[http://docs.python.org/distutils/index.html](http://docs.python.org/distutils/index.html)

---

### Post by nvteighen on 2009-11-29
> **oldfred said:**
> I have not used it but this seems to cover some of your questions:

[http://docs.python.org/distutils/index.html](http://docs.python.org/distutils/index.html)
Distutils is something a bit different, but it can be of help too.

---

