---
title: "Installing Eset NOD32 says install files or packages: Iibc6:i386, /lib/Id-linux.so.2"
date: 2018-10-06
forum: New to Ubuntu
---

### Post by cutupguy on 2018-10-06
My first day with any Linux and already stuck. :confused:

I just installed Ubuntu 64-bit 18.04.1,which is running on VMware 11,
which is running on MacOS Mojave 10.14.

No problem until I try to install ESET NOD32 from the Eset web site.  That install stops with this message;



Please install the following files or packages: Iibc6:i386, /lib/ld-
[SIZE=1] linux.so.2

What do I do now?
Thanks for your help![/SIZE]

---

### Post by Holger_Gehrke on 2018-10-07
Those are two very basic parts of a Linux system (the loader for dynamic libraries and the c-runtime). I doubt your system would run if you did not have them. But the suffix ':i386' tells us the real problem: it's a 32 bit program and you have a 64 bit system. So you can either go back to the website and download the 64 bit version or set up your system to work with 32 bit programs (on the command line: 'sudo dpkg --add-architecture i386; sudo apt-get install libc6:i386').

Holger

---

### Post by cutupguy on 2018-10-08
THANK YOU, Holger!  I would have not found that in a hundred years.
Al

---

