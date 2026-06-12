---
title: "Computer turned off when installing g++"
date: 2010-05-02
forum: Programming Talk
---

### Post by dmp1ce on 2010-05-02
I was installing g++ through Synaptic Package Manager when my computer overheated and turned off.  Now I cannot install or remove g++.  I get the following error when trying to remove the package.  Any ideas on how to fix this?

(Reading database ... 274817 files and directories currently installed.)
Removing g++ ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing g++ (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by MadCow108 on 2010-05-02
try executing apt-get install -f
this will attempt to fix your package database

---

### Post by dmp1ce on 2010-05-02
I think I figured it out.  I had to go into the /var/lib/dpkg/status file and remove all entries of g++.

---

