---
title: "Nemesis Installation is My Nemesis"
date: 2013-01-30
forum: Programming Talk
---

### Post by dansofe0r on 2013-01-30
Good day everyone. I'm sure you're all working on interesting and challenging projects that experienced programmers such as yourselves no doubt have. 

I've been trying for quite a while to install nemesis without success. When I try to use the command :
```
/nemesis-1.4$ ./configure --with-libnet
```it returns:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
checking for gcc option to accept ANSI C... none needed
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for an ANSI C-conforming const... yes
checking for gawk... (cached) mawk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for fabs in -lm... yes
checking for inet_ntoa in -lnsl... yes
checking for socket in -lsocket... no
checking for hstrerror in -lresolv... yes
checking for libnet_build_ip in -lnet... no

[B]   ERROR!  Libnet library not found, go get it from
   http://www.packetfactory.net/projects/libnet/
   or use the --with-libnet-* options, if you have it installed
   in unusual place[/B]

```I have already installed libnet 1.0.2a because I know that nemesis uses that version of libnet. It is sitting in the 'Downloads' folder now. 

I have also tried including the directory after using --with-libnet but maybe I am not entering the directory or syntax correctly. Also installed libnet1-dev with the Ubuntu Software Center. 

Perhaps there is a newer nemesis-like program that could be used. I am aware that it is no longer in development. If not, I would certainly appreciate any insights or help. :)

---

### Post by steeldriver on 2013-01-30
try installing the corresponding libnet1**-dev** package
```

$ apt-cache show libnet1-dev
Package: libnet1-dev
Priority: optional
.
.
 .
 libnet features portable packet creation interfaces at the IP layer
 and link layer, as well as a host of supplementary functionality.
 .
 Using libnet, quick and simple packet assembly applications can be
 whipped up with little effort. With a bit more time, more complex
 programs can be written (Traceroute and ping were easily rewritten
 using libnet and libpcap).
 .
[B] This package contains the files needed to compile and link programs
 that use libnet.
[/B].
.
.
```

---

### Post by dansofe0r on 2013-01-30
I installed libnet1-dev with the Ubuntu Software Center before but I forgot to mention that. Would I need to use the terminal to install it?

---

### Post by Zugzwang on 2013-01-31
> **dansofe0r said:**
> I installed libnet1-dev with the Ubuntu Software Center before but I forgot to mention that. Would I need to use the terminal to install it?

No, that doesn't matter. Please verify that the files "/usr/include/libnet.h" and "/usr/lib/libnet.a" are in place. For that, please copy&paste the output of the command "ls -la /usr/include/libnet.h /usr/lib/libnet.a" here.

---

### Post by dansofe0r on 2013-02-01
```

$ ls -la /usr/include/libnet.h /usr/lib/libnet.a
-rw-r--r-- 1 root root   4281 Oct  4 20:23 /usr/include/libnet.h
-rw-r--r-- 1 root root 159552 Oct  4 20:23 /usr/lib/libnet.a


```

---

