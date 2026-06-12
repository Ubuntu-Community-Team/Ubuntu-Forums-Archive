---
title: "setting up gcc"
date: 2005-11-04
forum: Programming Talk
---

### Post by cherryos on 2005-11-04
Hi, i'm setting up gcc and i got this error,

root@ubuntu:/usr/gcc/gccbuild# /usr/gcc/gcc-4.0.2/configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

I was wondering how to get rid of it.

---

### Post by rock freak on 2005-11-04
you should just be able to download gcc from the synapatic package manager just search for gcc

and dont forget the gcc lib called libgcc i belive. that should install it for you.


to test if its worked just  open ypu the terminal and type gcc and you should get this

> gcc: no input files

hope this works/helps

Ollie

---

### Post by mo_x on 2005-11-04
Are you trying to compile the compiler without a compiler?
Just install the build-essential package.
```
sudo apt-get install build-essential
```

---

### Post by cherryos on 2005-11-04
yeah, you were both right, i used the synaptic package manager to install apache and apt-get for gcc. but now, how do i access apache, where is the directory for it? when i type localhost into the address bar i get the apache successfully installed page.

---

### Post by rock freak on 2005-11-04
excellent gald i could help. In regards to the apache im not sure cant rember i had it installed but neva got round to using it as got a websever i use!

---

