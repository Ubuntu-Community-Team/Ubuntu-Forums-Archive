---
title: "Unable to locate dh_make ?   - why ?"
date: 2011-09-30
forum: Packaging and Compiling Programs
---

### Post by Andre-D on 2011-09-30
Why ? - this is a plain 11.04 
I plan to make a .deb, so afaik , I need dh_make

sudo apt-get install dh_make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dh_make


my essential part of sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

---

### Post by SevenMachines on 2011-09-30
```
$ apt-file search /usr/bin/dh_make          
cli-common-dev: /usr/bin/dh_makeclilibs
debhelper: /usr/bin/dh_makeshlibs
dh-make: /usr/bin/dh_make

$ sudo apt-get install dh-make
```
Note the hyphen in the dh-make package name, *not* an underscore.

---

### Post by Andre-D on 2011-09-30
thank you, the underscore was the problem.. :)

---

