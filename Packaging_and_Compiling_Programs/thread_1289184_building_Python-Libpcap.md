---
title: "building Python-Libpcap"
date: 2009-10-12
forum: Packaging and Compiling Programs
---

### Post by Tobywuk on 2009-10-12
Hello,

I am trying to install python-libpcap

I have followed the readme by doing an apt-get install libpcap-dev to install libpcap and then running the python ./setup.py file for python-libpcap.

pcap.c:118:20: error: Python.h: No such file or directory

i get a load of build errors with pcap.c:xxx error's
and finally a gcc failed with exit status 1 message.

Im using ubuntu 9.04 64bit vershion.

anyone had experiance with pyLibPcap and can help?

thanks

---

### Post by Tobywuk on 2009-10-12
Just installed it all through the repositories

apt-get install libpcap-dev
apt-get install python-libpcap


I would still be interested in any comments with regards to the manual compiling above though :)

---

### Post by dinxter on 2009-10-12
you're missing build dependencies, you can either look at the requirements in the source code, or you can get the build dependencies for a ubuntu package by
$ sudo apt-get build-dep <package>
though these may not be the same as the source code requirements if downloaded from somewhere else they usually are

---

