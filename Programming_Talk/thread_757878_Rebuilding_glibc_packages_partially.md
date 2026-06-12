---
title: "Rebuilding glibc packages partially"
date: 2008-04-17
forum: Programming Talk
---

### Post by evcosta on 2008-04-17
I am building glibc 2.5 (Feisty) packages from apt-getted sources. I found it builds every possible library by default. For example I do not want profile, debug, udeb. One of the build logs (log-test-i486-linux-gnu-libc) is showing an error that AFAICT is related to the profile libraries build (seen at a Redhat forum old message). Also I do not want to spend time building the amd64 and xen libraries. 

I deleted some entries from debian/control but it did not work. I tried to find information in man pages as well as the internet with no success. Where can I control what is built?

Any suggestion or pointer is welcome.

Thank you very much in advance.

Elder.

---

### Post by evcosta on 2008-04-17
It is off topic here. It is a pitty one cannot delete their messages. I apologyze.

---

