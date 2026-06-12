---
title: "Error compiling"
date: 2013-11-13
forum: Packaging and Compiling Programs
---

### Post by peterson.justin on 2013-11-13
I  have been attempting to install Gazelle using this guide: [https://github.com/WhatCD/Gazelle/wiki/Installation-Walkthrough---written-Ubuntu-12.04--Nov.2012](https://github.com/WhatCD/Gazelle/wiki/Installation-Walkthrough---written-Ubuntu-12.04--Nov.2012)

I have followed it word for word, but when I get to this part:

sudo ./configure --with-mysql-lib=/usr/lib/x86_64-linux-gnu/

It gives me this error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for g++... g++
checking whether the C++ compiler works... no
configure: error: in `/ocelot':
configure: error: C++ compiler cannot create executables
See `config.log' for more details

All the forums I have read state that I need to install the **build-essential** package to pull in the compilers. I've done this. It still persists.
I'm not sure what to do next. Any ideas? Here's some things that it says in the config.log:

[http://imgur.com/8F2yHmA](http://imgur.com/8F2yHmA)

Here's the Config file:

[http://imgur.com/TQNLGYF](http://imgur.com/TQNLGYF)

---

### Post by steeldriver on 2013-11-13
What architecture are you actually trying to build for/on? it looks like you are following instructions applicable to x86_64 but are actually building on a 32-bit machine

---

### Post by peterson.justin on 2013-11-13
It's on a Ubuntu 12.04 64-bit server.

---

