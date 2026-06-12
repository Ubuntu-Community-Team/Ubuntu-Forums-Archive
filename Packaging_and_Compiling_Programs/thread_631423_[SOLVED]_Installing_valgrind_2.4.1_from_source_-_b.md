---
title: "[SOLVED] Installing valgrind 2.4.1 from source - best practices?"
date: 2007-12-04
forum: Packaging and Compiling Programs
---

### Post by Rudi Völler on 2007-12-04
Hi all, 

Im installing Valgrind 2.4.1 from source on Kubuntu 7.10 and when I run the ./configure command, i get: 
```
...
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for perl... /usr/bin/perl
checking for gdb... /usr/bin/gdb
checking for a supported version of gcc... ok (gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2))
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for a supported CPU... ok (i686)
checking for a supported OS... ok (linux)
checking for the kernel version... 2.6 family (2.6.22-14-generic)
checking for a supported CPU/OS combination... ok (i686-linux)
checking for egrep... grep -E
checking the glibc version... unsupported version
**configure: error: Valgrind requires the glibc version 2.1, 2.2, 2.3 or 2.4**
```
And I have to use this version of Valgrind for compatibility with another program I am using. build-essentials is also installed

So my question is, what are the best practices for installing old programs from source to insure that it doesn't damage my setup (e.g. should I install to other directories than the default ones?) and how do I solve this version issue with glibc? 

Thanx!

---

### Post by swerner on 2007-12-04
Try the following:

```
apt-get build-dep valgrind
```

This will download all the dependencies required to build valgrind.  Make sure that you have all the 'deb-src' lines uncommented in your /etc/apt/sources.list file, and remember to run 'apt-get update' after making any changes to the sources.list file.

---

### Post by Rudi Völler on 2007-12-05
> **swerner said:**
> Try the following:

```
apt-get build-dep valgrind
```

This will download all the dependencies required to build valgrind.  Make sure that you have all the 'deb-src' lines uncommented in your /etc/apt/sources.list file, and remember to run 'apt-get update' after making any changes to the sources.list file.

Thanks for the reply!

But I need version 2.4.1 and the repositories contain version 3.2.3. I have tried to install that version and the install works but i cant use that version. 
I have downloaded the source files for glibc version 2.4 but I am wondering if it is safe to install that version since Valgrind 2.4.1 requires it? And if so, should I install in into f.ex. /home/myUserName/bin and add that to my PATH?

---

### Post by swerner on 2007-12-05
That may work.  How about downloading an older version of valgrind, I found 2.4.0 [here]("http://ftp.debian.org/debian/pool/main/v/valgrind/").  Download the deb and install it.  I don't know how specific you need to be with the version, but I presume 2.4.0 may work.

Otherwise I don't know what to do.

---

### Post by Rudi Völler on 2007-12-05
Problem solved!

Of course I should have tried installing a .deb package instead of installing from source. Then i used dselect to put the Valgrind package on hold and everything works!

Thanks for the help swerner!

---

