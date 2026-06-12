---
title: "[SOLVED] ./configure problem (can't find c++ compiler)"
date: 2008-02-23
forum: Packaging and Compiling Programs
---

### Post by Griff on 2008-02-23
I have the gcc c++ compiler package installed yet ./configure can't seem to find it.  Also 'make distclean' doesn't seem to work.  Any ideas what is going on?  Here's the code:

./configure
```

checking for true... /bin/true
checking for false... /bin/false
configuring for bacula 2.2.8 (26 January 2008)
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
configure: error: Unable to find C++ compiler

```
make distclean
```

make: *** No rule to make target `distclean'.  Stop.


```

---

### Post by Vorian on 2008-02-23
care to post your rules file?

---

### Post by Griff on 2008-02-23
> **Vorian said:**
> care to post your rules file?
Sorry but where is this file and what is the exact name?

---

### Post by shad0w_walker on 2008-02-23
It doesn't look like you have any compiling tools installed. Easiest way to get around this is to install build essential.

Open up a terminal and run:

```
sudo aptitude install build-essential
```

That will install the needed bits and pieces for most compiling needs.

---

### Post by Griff on 2008-02-23
Alright I figured it out.  I had an incorrect path specified for g++.  g++ didn't exist because g++ couldn't be found.  Thanks for the quick responses guys.

ps: and 'make distclean' didn't work because I hadn't got far enough running ./configure for anything to be made.

---

