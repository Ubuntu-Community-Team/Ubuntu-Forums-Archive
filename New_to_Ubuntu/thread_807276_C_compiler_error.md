---
title: "C compiler error"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Colonel Forbin on 2008-05-25
Im trying to configure shntool from source, and shorten, and when i do ./configure i get this error:

forbin@Colonel-Forbin:~/Desktop/shorten-3.6.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
forbin@Colonel-Forbin:~/Desktop/shorten-3.6.1$ 

I'm not sure what to do now. Can anyone help?

---

### Post by Sinkingships7 on 2008-05-25
Do you have build-essential installed?

If not, type
```
sudo apt-get install build-essential
```
into the terminal to install it, then try to ./configure and see if the problem persists.

---

