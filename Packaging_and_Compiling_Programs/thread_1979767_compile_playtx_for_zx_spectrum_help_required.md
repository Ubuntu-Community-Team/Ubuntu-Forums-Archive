---
title: "compile playtx for zx spectrum: help required"
date: 2012-05-14
forum: Packaging and Compiling Programs
---

### Post by blesbok on 2012-05-14
Hi everyone, I have untarred  playtzx-0.12 for the ZX Spectrum. The file, configure, wasn't executable so it was chmod +x'd

after ./configure:

```
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether lots of warnings requested... no
updating cache ./config.cache
creating ./config.status
creating Makefile
creating config.h
```

As I understand, this software is written for another environment like Fedora rather than Debian. How can I get it working in Precise 12.04 LTS?

The ultimate goal is to produce mp3 files from the tzx files. If it's possible to download Spectrum games as mp3 (without flash), please tell me where to find them.

---

### Post by oldos2er on 2012-05-14
Moved to Packaging and Compiling Programs.

---

### Post by MadCow108 on 2012-05-14
nothing failed yet.

now you need to type *make* to compile it, and *make install* if you want to install it

I recommend running:
```
./configure --prefix=$HOME/tmp/local
make
make install
```
which will install it in $HOME/tmp/local/bin/
by default it would go into /usr/local, which I personally do not recommend as it needs root rights opening up the possibility of you breaking your system

---

### Post by blesbok on 2012-05-14
MadCow108 wrote:

> nothing failed yet.

now you need to type make to compile it, and make install if you want to install it

Well make had been attempted unsuccessfully. In the meantime this was done:

```
apt-get install build-essential
apt-get update && apt-get upgrade
apt-get install automake
```

And... your contribution got it working! ):P Thanks for the configure tip too. As one for orthodoxy, I must just ask, why the tmp (temporary) and not just prefix=$HOME/local? ($HOME/local is not yet in my home directory.)

Thanks again MadCow108 and oldos2er.

---

### Post by MadCow108 on 2012-05-15
$HOME/local is fine too. Where you put is is up to you (but never directly in /usr thats package manager land).

---

