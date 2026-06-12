---
title: "no c compiler found - BS!"
date: 2005-02-11
forum: Programming Talk
---

### Post by sharkzf6 on 2005-02-11
Tried to install a program, this is what I got after running *sudo ./configure* from the unzipped package directory:

[b]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/b]

According to synaptic GCC 3.3 and 3.4 are installed. I don't know beans about programming so I thought I put a query in this forum. Thanks for any help.

---

### Post by az on 2005-02-11
You need to install build-essential.

It is one package that brings in all you need.

---

### Post by sharkzf6 on 2005-02-11
[QUOTE=azz]You need to install build-essential.

It is one package that brings in all you need.[/QUOTE]
Thanks!  :D

---

### Post by BJinMontreal on 2007-03-05
I went through steps to install GnuCash with the C compiler erroras well. I used the build essential command and still am getting errors.  The latest is telling me possibly GLIB is incorrectly installed. configure: error: GLIB>= 2,4 is required to build Gnucash; please make sure you have the development headers installed.

How do I install the latest GLIB?

---

### Post by po0f on 2007-03-05
BJinMontreal,

Install libglib2.0-dev:

```
$ sudo apt-get install libglib2.0-dev
```

---

