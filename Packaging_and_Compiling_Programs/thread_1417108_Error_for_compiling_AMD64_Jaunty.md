---
title: "Error for compiling AMD64 Jaunty"
date: 2010-02-26
forum: Packaging and Compiling Programs
---

### Post by ras123 on 2010-02-26
Hi,
I cannot compile the following packages for AMD64 Jaunty, other version can be compiled. Here is the error report
[https://launchpad.net/~mec2009/+archive/ppa/+build/1533329/+files/buildlog_ubuntu-jaunty-amd64.ngspice_19-0ubuntu2~jaunty4_FAILEDTOBUILD.txt.gz]("https://launchpad.net/%7Emec2009/+archive/ppa/+build/1533329/+files/buildlog_ubuntu-jaunty-amd64.ngspice_19-0ubuntu2%7Ejaunty4_FAILEDTOBUILD.txt.gz")
It says that implicit pointer conversion, so I added patches, still it has the same errors,

Now Solved, I think there is problem to set the value of HAVE_UNISTD_H, by the compiler for the AMD64/Jaunty

---

