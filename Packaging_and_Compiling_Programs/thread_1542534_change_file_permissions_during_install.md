---
title: "change file permissions during install"
date: 2010-07-30
forum: Packaging and Compiling Programs
---

### Post by puzzler995 on 2010-07-30
I have written a python program that has a Shell Script in the directory /usr/bin/ The problem is, with the .deb file I have created, when it is installed, the shell script requires sudo to run. How can I change the shell script's permissions during install? Or is there somewhere else I can put it?
For the .deb file go to [THIS]("https://sourceforge.net/projects/math-helper/") SourceForge Project
Thanks,
Puzzler995

---

### Post by SevenMachines on 2010-07-31
Your shell script doesnt need sudo to run, it needs to have executable file permissions. debhelper usually sorts this out during building the package though i'm suspecting this .deb file is manually created(?). But in any case, at the moment you have
$ ls -l /usr/bin/math-helper 
-rw-r--r-- 1 <user> <user> 80 2010-07-30 20:36 /usr/bin/math-helper

Its user owned and read-write for owner, read for group and others
Files in /usr/bin/ are user root and group root for the most part
and user read-write-execute, group and group read-execute

# Make Owner and group root
$ sudo chown root.root /usr/bin/math-helper

# Set the correct permissions
$ sudo chmod 755  /usr/bin/math-helper

---

