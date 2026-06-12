---
title: "problem installing libtool on ubuntu"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by nawaz1 on 2012-08-29
hii
i try to install libtool for ./bootstrap for openocd
but got error plz help



nawazbaig@ubuntu:~/openocd$ sudo apt-get install libtool

[sudo] password for nawazbaig: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

You might want to run 'apt-get -f install' to correct these:

The following packages have unmet dependencies:
 libtool : Depends: autotools-dev but it is not going to be installed
           Recommends: libltdl-dev but it is not going to be installed
 xscale-elf-binutils:i386 : Depends: libc6:i386 (>= 2.5-0ubuntu1) but it is not going to be installed
 
xscale-elf-gcc:i386 : Depends: libc6:i386 (>= 2.5-0ubuntu1) but it is not going to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

