---
title: "FreeSWITCH: While Processing Program 'check_dlopen_sofia'"
date: 2010-07-17
forum: Packaging and Compiling Programs
---

### Post by GraysonPeddie on 2010-07-17
FreeSWITCH version: 1.0.6 (from GIT tree)

Direct from GIT:

```
./bootstrap.sh # <- This is what I'm having trouble with.
./configure
make
sudo make install
sudo make uhd-sounds-install
sudo make uhd-moh-install
sudo make samples
```

./bootstrap.sh:

```
grayson@server:~/src/freeswitch$ ]automake: compiling `check_dlopen_sofia.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
tests/Makefile.am:37:   while processing program `check_dlopen_sofia'
```

It's been sitting there for about an hour now and I don't know what's going on.

I did compile and install FreeSWITCH, but the build seems to be incomplete once I stopped at this part where it took me a lot of time...

The reason why I have to do this over again, is because I'm trying to compile mod_managed and it expects libfreeswitch.la within the root directory of FreeSWITCH where Makefile resides.

---

### Post by SevenMachines on 2010-07-17
That should be just an automake warning (about portability i think) and non-fatal. does the compile not proceed along happily anyway?
you can quickly check by running make in libs/sofia-sip/tests, if this goes without problems i'd ignore it.

---

### Post by GraysonPeddie on 2010-07-17
In the previous thread where you provided 3 options, ./configure and make did not help since it does not appear to build all the sources and include libfreeswitch.la in the base directory where Makefile resides in. So in that case, I do "ln -s $(locate libfreeswitch.la)" and I got it symlinked so I will build mod_managed and give it a try.

Thanks.

Update:

Apparently, I switched from compiled version of Mono to deb version of Mono (2.6.3) in Ubuntu 10.10 Alpha 2 and it works.

I might try out mod_managed and see what it does.

---

### Post by extnct on 2010-08-25
Hi,

I'm also installing from the GIT tree ([http://wiki.freeswitch.org/wiki/Installation_Guide#Obtaining_the_Source_Code](http://wiki.freeswitch.org/wiki/Installation_Guide#Obtaining_the_Source_Code)) and the bootstrap script hangs forever on that line.

> libsofia-sip-ua-glib/su-glib/Makefile.am: installing `./depcomp'
lib/Makefile.am: installing `./depcomp'
automake: compiling `check_dlopen_sofia.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
tests/Makefile.am:37:   while processing program `check_dlopen_sofia'
^C


I followed SevenMachine's advice:
> /usr/src/freeswitch/libs/sofia-sip/tests# make
make: *** No targets specified and no makefile found.  Stop.

I also ran updatedb && locate libfreeswitch.la, but it doesn't bring up any results.

Does anyone know what could be wrong?

---

### Post by extnct on 2010-08-25
Followed the Quick & Dirty method it compiled without issues [http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install](http://wiki.freeswitch.org/wiki/Quick_and_Dirty_Install)

Not sure what the problem was...

Edit: Actually even this install has issues, some modules (e.g. mod_spidermonkey.so) aren't found and when I test the Music On Hold extension I get [ERR] switch_core_file.c:122 Invalid file format [silence_stream] for [2000]!

---

