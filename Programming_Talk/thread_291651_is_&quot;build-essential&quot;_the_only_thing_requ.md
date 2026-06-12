---
title: "is &quot;build-essential&quot; the only thing required to compile ?"
date: 2006-11-02
forum: Programming Talk
---

### Post by syxbit on 2006-11-02
some websites indicate all you need is to run
```
sudo apt-get install build-essential
```


others also list these 2.
```
sudo apt-get install manpages-dev autoconf automake libtool
sudo apt-get install flex bison gcc-doc g++
```

what's the difference ?
thanks

---

### Post by hod139 on 2006-11-02
build-essential will install (from packages.ubuntu.com):[LIST]
[*][dpkg-dev]("http://packages.ubuntu.com/dapper/utils/dpkg-dev") (>= 1.13.5)package building tools for Debian
[*][g++]("http://packages.ubuntu.com/dapper/devel/g++") (>= 4:4.0)The GNU C++ compiler
[*][gcc]("http://packages.ubuntu.com/dapper/devel/gcc") (>= 4:4.0)The GNU C compiler
[*][libc6-dev]("http://packages.ubuntu.com/dapper/libdevel/libc6-dev")GNU C Library: Development Libraries and Header Files
[*][make]("http://packages.ubuntu.com/dapper/devel/make")The GNU version of the "make" utility.[/LIST]These packages will allow you to build C or C++ code.

> **syxbit said:**
> others also list these 2.
```
sudo apt-get install manpages-dev autoconf automake libtool
sudo apt-get install flex bison gcc-doc g++
```what's the difference ?
thanks
manpages-dev installs the man pages for the development tools.  autoconf, automake, and libtool are all required for [autotools]("http://sources.redhat.com/autobook/")

Flex and bison you most likely will not need in your development, I've never used them.  gcc-doc is the documentation for the gcc compiler.  g++ is redundent with build-essential.

In closing, you may need the autotools packages as many source distributions use it, but build-essential should be sufficient if you just wish to program c or c++.

---

### Post by syxbit on 2006-11-03
very helpful
thanks

---

