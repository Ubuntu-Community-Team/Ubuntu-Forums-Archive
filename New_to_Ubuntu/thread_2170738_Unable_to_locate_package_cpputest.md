---
title: "Unable to locate package cpputest"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by eedev on 2013-08-27
this is my release:

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


When I try and install cpputest (calling this command: *sudo apt-get install cpputest)*

I get this messages:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cpputest

How to get rid of it?
Thanks

---

### Post by tgalati4 on 2013-08-27
tgalati4@Mint14-Extensa ~ $ apt-cache search cppu
libcppunit-1.12-1 - Unit Testing Library for C++
libcppunit-dev - Unit Testing Library for C++
libcppunit-doc - Unit Testing Library for C++
libcppunit-subunit-dev - SubunitTestProgressListener for CPPUnit - Development headers
libcppunit-subunit0 - SubunitTestProgressListener for CPPUnit - C++ shared library
uno-libs3 - LibreOffice UNO runtime environment -- public shared libraries
uno-libs3-dbg - LibreOffice UNO runtime environment -- public shared library debug symbols
cpputest - C/C++ based unit test framework &#8212; main package
cxxtest - lightweight xUnit-like framework for C/C++ applications
libcpputest-dev - C/C++ based unit test framework &#8212; headers and static libraries
libcunit1 - Unit Testing Library for C
libcunit1-dev - Unit Testing Library for C -- development files
libcunit1-doc - Unit Testing Library for C -- documentation
libcunit1-ncurses - Unit Testing Library for C (ncurses)
libcunit1-ncurses-dev - Unit Testing Library for C (ncurses) -- development files
libqxcppunit-dev - A Qt4-based GUI for running tests with CppUnit - development files
libqxcppunitd1 - A Qt4-based GUI for running tests with CppUnit

What is the output of:

```
apt-cache policy cpputest
```

The package exists in 12.10:

tgalati4@Mint14-Extensa ~ $ apt-cache policy cpputest
cpputest:
  Installed: (none)
  Candidate: 3.1-2
  Version table:
     3.1-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by bkline on 2013-08-27
That package wasn't included in the Ubuntu repositories until one version after yours (12.10).  See [http://www.ubuntuupdates.org/pm/cpputest](http://www.ubuntuupdates.org/pm/cpputest)

You could build from source:

[http://cpputest.github.io/](http://cpputest.github.io/)

---

