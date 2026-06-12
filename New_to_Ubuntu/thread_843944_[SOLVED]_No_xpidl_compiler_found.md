---
title: "[SOLVED] No xpidl compiler found?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by RohanC on 2008-06-28
I have tried searching for an answer to this but am having no luck. I am trying to install mplayer plugin as per instructions here: [http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)
When I attempt './configure --enable-gtk1 --with-mozilla-home=/usr/lib/iceweasel --with-gecko-sdk=/home/rohan/xulrunner-sdk' it gives the following result:
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
Using new (v1.7+) gecko-sdk
checking for xpidl... no
configure: error: xpidl compiler not found
Any help appreciated.

---

### Post by dizee on 2008-06-28
the package mozilla-mplayer is available in ubuntu's repos and does the same thing. there's no need to compile from source unless you really need the newest version.

---

### Post by RohanC on 2008-06-28
All that hair tearing for naught. Thankx dizee.

---

### Post by g_rus on 2009-02-23
I have the same problem 
...
Using new (v1.7+) gecko-sdk
checking for xpidl... no
configure: error: xpidl compiler not found

But I need te compile, because I use Opera Browser, and mplayer plugin must be compile with Gecko path. 

Because with mplayer plugin from repositories, firefox and Seamonkey worx perfectly, but in Opera, the sound work but image is very small, liko some pixels!! very, very small.

---

### Post by Piraja on 2009-10-04
> **g_rus said:**
> I have the same problem 
...
Using new (v1.7+) gecko-sdk
checking for xpidl... no
configure: error: xpidl compiler not found

But I need te compile, because I use Opera Browser, and mplayer plugin must be compile with Gecko path.
The same here... so *bump*

---

### Post by migel_wimtore on 2010-03-14
bump

---

### Post by drgr33n on 2010-03-22
if you need to compile from source.

```


cpan CORBA::HTML
cpan CORBA::IDL
cpan CORBA::XPIDL


```

---

