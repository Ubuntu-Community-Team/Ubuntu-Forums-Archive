---
title: "universal socket library"
date: 2009-01-11
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-11
is there a socket library in C++ that will work on all platforms (documentation or anything about irc bots in C/C++ is helpful too)

---

### Post by Zugzwang on 2009-01-11
Well, you can for example use wxWidgets or also Qt. Both libraries have multi-platform networking support for at least Linux, Windows and Mac.

Personally I find Qt a little bit easier to use as its official examples are very helpful but by using it you are stuck with the GPL (if that matters) ... except if you buy a license.

---

### Post by jimi_hendrix on 2009-01-11
that it?

---

### Post by public_void on 2009-01-11
[C++ Sockets Library]("http://www.alhem.net/Sockets/"), has good documentation and works on Linux and Windows.

---

### Post by wmcbrine on 2009-01-11
(never mind... please delete)

---

### Post by jimi_hendrix on 2009-01-11
> **public_void said:**
> [C++ Sockets Library]("http://www.alhem.net/Sockets/"), has good documentation and works on Linux and Windows.

will i need to change code for it to run on linux? if i write it for windows that is...

---

### Post by jmartrican on 2009-01-11
Have you looked at boost::asio?  I started using it and never looked back.  It lets you do asynch IO on a socket, which will eliminate blocking.

---

### Post by jimi_hendrix on 2009-01-11
boost is giving me a hard time installing :(

---

### Post by jmartrican on 2009-01-11
I've gone through some headaches in the past with it.  There was one issue that popped up where it was known and there were forum entries on it, but sinc ethen i installed it version 1.35 and 1.27 on Ubuntu 8.04 without a problem.  Post the issue and maybe we can help.

---

### Post by dribeas on 2009-01-12
> **jimi_hendrix said:**
> boost is giving me a hard time installing :(

How come? I have used boost both from code and from ubuntu, debian and redhat packages without problems. In debian based systems you will need to install all libboost packages, but there could be a metapackage that depends on the others... would need to check.

---

