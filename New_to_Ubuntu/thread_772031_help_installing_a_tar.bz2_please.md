---
title: "help installing a tar.bz2 please"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by MangasColoradas on 2008-04-28
```
stone@ubuntu:~$ cd '/home/stone/Documents/murrine-0.53.1' 
stone@ubuntu:~/Documents/murrine-0.53.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
stone@ubuntu:~/Documents/murrine-0.53.1$ make
make: *** No targets specified and no makefile found. Stop.
stone@ubuntu:~/Documents/murrine-0.53.1$ 

```

I have followed this guide [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

> When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (Important! If you find packages in Synaptic named almost the same but with a -dev extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways: 

I thought I had followed it correctly but it seems not!

---

### Post by Michael.Godawski on 2008-04-28
hi
I do not know if this is the same package but try to download the deb file from here:

[https://launchpad.net/ubuntu/gutsy/i386/gtk2-engines-murrine/0.53.1-0ubuntu2](https://launchpad.net/ubuntu/gutsy/i386/gtk2-engines-murrine/0.53.1-0ubuntu2)

---

### Post by thisismalhotra on 2008-04-28
Here this will help

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also install package called build-essential from synaptic.

---

### Post by MangasColoradas on 2008-04-28
Thanks Michael, I really want to work out how to build it thanks.

Thanks thisis, installing build-essentials seems to have helped, it is telling me I am missing a dependency, which is a start but the dependencies need dependancies now lol and its just going on and on.

I should be able to do it now I have build-essentials I think.

BTW the link you gave is the one I am using, it makes it look easier than its proving to be!

---

### Post by Tatty on 2008-04-28
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) this may help

---

### Post by zvacet on 2008-04-28
Delete folder you get by decompressing tar.bz2 file and start from beginning.

```
sudo apt-get build-dep packagename
```

This will get all dependencies you need.Now extract tar.bz2 file and start compile.

---

### Post by MangasColoradas on 2008-04-28
Thanks everyone, the funny thing is...it was already installed. :mad:

I have learned some stuff though so thankyou. :)

---

