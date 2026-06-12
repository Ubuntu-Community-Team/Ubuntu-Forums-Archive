---
title: "g++ scons libraries installation"
date: 2014-02-12
forum: Programming Talk
---

### Post by babakflame on 2014-02-12
Dear Buddies

I have g++ on my system (ubuntu 11.10)
I have used this directive in terminal to make sure the following packages are on my system:```

g++ scons libboost-all-dev libsundials-serial-dev subversion libblas-dev liblapack-dev

``` 
what I got in terminal was:

```
babak@babak-VPCEA26FG:~/FlameletFOAM$  g++ scons libboost-all-dev libsundials-serial-dev subversion libblas-dev liblapack-dev
g++: error: scons: No such file or directory
g++: error: libboost-all-dev: No such file or directory
g++: error: libsundials-serial-dev: No such file or directory
g++: error: subversion: No such file or directory
g++: error: libblas-dev: No such file or directory
g++: error: liblapack-dev: No such file or directory
g++: fatal error: no input files
compilation terminated.


```

Does anybody know how can I install these libraries?

 Best Regards
   Bobi

---

### Post by Bachstelze on 2014-02-12
You very much need to review how to [install software]("https://help.ubuntu.com/community/InstallingSoftware"). ;)

(What you want here is probably *apt-get*.)

---

### Post by babakflame on 2014-02-12
Dear Buddies

 I even installed scons but the problem still exists: 

```

babak@babak-VPCEA26FG:~$ sudo apt-get install scons
[sudo] password for babak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  scons
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 504 kB of archives.
After this operation, 2,339 kB of additional disk space will be used.
Get:1 http://ir.archive.ubuntu.com/ubuntu/ oneiric/main scons all 2.0.1-2 [504 kB]
Fetched 504 kB in 6s (80.6 kB/s)                                               
Selecting previously deselected package scons.
(Reading database ... 367583 files and directories currently installed.)
Unpacking scons (from .../archives/scons_2.0.1-2_all.deb) ...
Processing triggers for man-db ...
Setting up scons (2.0.1-2) ...
babak@babak-VPCEA26FG:~$ scons --version
SCons by Steven Knight et al.:
    script: v2.0.1.r5134, 2010/08/16 23:02:40, by bdeegan on cooldog
    engine: v2.0.1.r5134, 2010/08/16 23:02:40, by bdeegan on cooldog
Copyright (c) 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010 The SCons Foundation
babak@babak-VPCEA26FG:~$  g++ scons libboost-all-dev libsundials-serial-dev subversion libblas-dev liblapack-dev
g++: error: scons: No such file or directory
g++: error: libboost-all-dev: No such file or directory
g++: error: libsundials-serial-dev: No such file or directory
g++: error: subversion: No such file or directory
g++: error: libblas-dev: No such file or directory
g++: error: liblapack-dev: No such file or directory
g++: fatal error: no input files
compilation terminated.

```

would somebody help me what should I do now?

  Regards
  Bobi

---

### Post by Bachstelze on 2014-02-12
You want to do

```
sudo apt-get install scons libboost-all-dev libsundials-serial-dev subversion libblas-dev liblapack-dev
```

---

### Post by babakflame on 2014-02-12
Dear Bachstelze

After running sudo apt-get for each of the softwares. I got this at the end lines for libboost-all-dev.


```
Get:2 http://ir.archive.ubuntu.com/ubuntu/ oneiric/universe libboost-math1.46-dev amd64 1.46.1-5ubuntu2 [1,599 kB]
Fetched 5,844 kB in 37s (156 kB/s)                                             
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/pool/main/g/gccxml/gccxml_0.9.0+cvs20110723-2_amd64.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

I tried sudo apt-get update but with no success. What is the directive for --fix-missing ? 

Can You help me how can I fix it?

   Regards
     Bobi

---

