---
title: "Wubi 32 and 64 confusion"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by HobbsTunaSandwich on 2012-01-17
Hi guys,

newcomer to linux here.

Here is my problem:

I need to be able to run two simulation software packages, which in turn are suppossed to be able to exchange data, using a virtual machine (PVM). As a first step I decided to check if they worked independently:

1. relap5.x: works fine

```
file relap5.x
``` returns:

ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.2.5, not stripped

2. parcs-v270m04r-amd64.x: cannot execute binary file

```
file parcs-v270m04r-amd64.x
``` returns:

ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

Now I had just downloaded (from this page: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer))  wubi, which installed ubuntu 11.10. 

Now apparently this resulted in the 32-bit version of Ubuntu ending on my computer, as indicated by:

```
getconf LONG_BIT
``` returns: 32

and the following entries in the config-file of the boot-folder:

```
CONFIG_X86_32=y
# CONFIG_X86_64 is not set
```This confuses me, since it was my impression that wubi would install the 64-bit version by default.
So to my questions:

1. Do I assume correctly that the presented evidence is enough to say that I indeed have the 32-bit
 version installed?
2. Is there a way to get Wubi to install a 64-bit version?
3. My intended end result is to have both files running, how I get there is not that important. Since I apparently got 1 32-bit software and 1 64-bit software (assuming I interpret the file-command results correctly?), what's easier, getting a 64-bit version to run on a 32-bit system or the other way round?
And how would I go about it?

Please assume, that you are dealing with somebody mildly retared, who, in fact, will have to be told to press the shiny, shiny button to make the spirits of computing perform their magic.

Thank you for your time and patience!

---

### Post by mcduck on 2012-01-17
> **HobbsTunaSandwich said:**
> 

1. Do I assume correctly that the presented evidence is enough to say that I indeed have the 32-bit
 version installed?
2. Is there a way to get Wubi to install a 64-bit version?
3. My intended end result is to have both files running, how I get there is not that important. Since I apparently got 1 32-bit software and 1 64-bit software (assuming I interpret the file-command results correctly?), what's easier, getting a 64-bit version to run on a 32-bit system or the other way round?
And how would I go about it?


1. Yes, it seems so.

2. I have no idea. I would suggest making a proper install instead of Wubi install anyway. Wubi is a decent tool for testing Ubuntu, if live-CD isn't enough but you aren't yet ready for a proper install, but in the long run a normal install will be more stable, more flexible, and less likely to develop problems.

3. Running 32-bit software on a 64-bit system works fine. Trying to do the opposite is impossible. So if you need to be able to run 64-bit executables (or both) your only option is to run a 64-bit operating system as well.

---

### Post by Frogs Hair on 2012-01-17
Wubi downloads and installs 64 bit by default and you have to do some work to wind up with 32 bit , so I don't know what happened there . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

