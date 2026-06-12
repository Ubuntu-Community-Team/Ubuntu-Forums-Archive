---
title: "Error in installing Sun JDK in 64 bit Server 10.0.4 LTS"
date: 2010-11-12
forum: Packaging and Compiling Programs
---

### Post by albertwt on 2010-11-12
Hi All,

I'm having problem in installing Sun Java JDK 6, I couldn't make it work in my Ubuntu 10.04 LTS Server 64 bit.

```
root@SSV:~# java
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
Try: apt-get install <selected package>

root@SSV:~# apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6-bin

root@SSV:~# add-apt-repository "deb http://archive.canonical.com/ lucid partner"The program 'add-apt-repository' is currently not installed.  You can install it by typing:
apt-get install python-software-properties

root@SSV:~# apt-get install python-software-properties
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  python-software-properties
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 30.8kB of archives.
After this operation, 1,126kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main python-software-properties 0.75.10.1 [30.8kB]
Fetched 30.8kB in 0s (223kB/s)
Selecting previously deselected package python-software-properties.
(Reading database ... 46404 files and directories currently installed.)
Unpacking python-software-properties (from .../python-software-properties_0.75.10.1_all.deb) ...
Processing triggers for man-db ...
Setting up python-software-properties (0.75.10.1) ...

Processing triggers for python-central ...

root@SSV:~# add-apt-repository "deb http://archive.canonical.com/ lucid partner"root@SSV:~# apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk           Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6-bin

root@SSV:~# apt-get install sun-java6-jre sun-java6-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

root@SSV:~#
```
 

can anyone assist me here please ?

Thanks.

---

### Post by SevenMachines on 2010-11-12
I dont have lucid or 64 bit but unless the packages/repository is broken then the following should work

> $ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
$ sudo apt-get update
$ sudo apt-get install sun-java6-jre sun-java6-jdk 

---

### Post by albertwt on 2010-11-12
> **SevenMachines said:**
> I dont have lucid or 64 bit but unless the packages/repository is broken then the following should work

Yes that does works, thanks for the help.

---

