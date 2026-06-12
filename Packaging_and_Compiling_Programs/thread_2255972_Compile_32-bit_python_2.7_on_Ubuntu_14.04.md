---
title: "Compile 32-bit python 2.7 on Ubuntu 14.04"
date: 2014-12-08
forum: Packaging and Compiling Programs
---

### Post by nomnom2 on 2014-12-08
Hi folks,

As the title states, I am trying to install python 2.7, 32-bit on Ubuntu 14.04. I don't see a 32-bit package in the repository, so I'm going about the route of building the package.

I have several 32-bit libraries installed, in particular: 

libc6-dev:i386, libx11-6:i386, libxext6:i386, libxft2:i386, libxcursor1:i386, libstdc++6:i386, libglib2.0-0:i386, libsm6:i386 (and probably a few more).

Following someone else's guidance I am trying to build python by:

$ CFLAGS=-m32 LDFLAGS=-m32 ./configure --prefix=/opt/Python2.7-32bits
checking for --enable-universalsdk... no
checking for --with-universal-archs... 32-bit
checking MACHDEP... linux3
checking EXTRAPLATDIR... 
checking machine type as reported by uname -m... x86_64
checking for --without-gcc... no
checking for gcc... gcc
checking whether the C compiler works... no
configure: error: in `/home/nomnom/Desktop/Python-2.7':
configure: error: C compiler cannot create executables
See `config.log' for more details.

I'm probably missing something silly, and need to specify a different compiler or pass another flag?

Anyways, if anyone has any ideas, the help would be much appreciated :)

Thanks!


-------------- edit --------------

This fixed it:

[FONT=Ubuntu Mono]apt-get install gcc-multilib g++-multilib[/FONT]

---

