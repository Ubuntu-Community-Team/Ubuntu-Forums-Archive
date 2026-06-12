---
title: "building minimo"
date: 2006-11-26
forum: Programming Talk
---

### Post by dbbolton on 2006-11-26
so, i'm trying to build my own linux-compatible version of minimo.

a few references:
[http://www.mozilla.org/projects/minimo/build.html](http://www.mozilla.org/projects/minimo/build.html)
[http://developer.mozilla.org/en/docs/Mozilla_Source_Code_Via_CVS](http://developer.mozilla.org/en/docs/Mozilla_Source_Code_Via_CVS)
[http://developer.mozilla.org/en/docs/Configuring_Build_Options#Using_a_.mozconfig_Configuration_File](http://developer.mozilla.org/en/docs/Configuring_Build_Options#Using_a_.mozconfig_Configuration_File)

here's my mozconfig file:
```
# Mozilla configuration file
# http://developer.mozilla.org/en/docs/Configuring_Build_Options#Using_a_.mozconfig_Configuration_File

. $topsrcdir/minimo/config/mozconfig

#########################
# these go to client.mk #
#########################
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
mk_add_options MOZ_CO_PROJECT=minimo

#########################
# these go to configure #
#########################
ac_add_options --enable-application=minimo

ac_add_options --enable-optimize 
# Enables the default compiler optimization options

ac_add_options --enable-default-toolkit=gtk2
# Graphics Toolkit

ac_add_options --enable-xft
# Font Rendering

ac_add_options --disable-static --enable-shared
ac_add_options --disable-js-static-build 
# Static build

```when i run "make -f client.mk build_all", i get this error:

> /usr/bin/ld: cannot find -lxpcom
collect2: ld returned 1 exit status
make[5]: *** [libpref.so] Error 1
make[5]: Leaving directory `/home/daniel/mozilla/obj-i686-pc-linux-gnu/modules/l ibpref/src'
make[4]: *** [libs] Error 2
make[4]: Leaving directory `/home/daniel/mozilla/obj-i686-pc-linux-gnu/modules/l ibpref'
make[3]: *** [libs_tier_necko] Error 2
make[3]: Leaving directory `/home/daniel/mozilla/obj-i686-pc-linux-gnu'
make[2]: *** [tier_necko] Error 2
make[2]: Leaving directory `/home/daniel/mozilla/obj-i686-pc-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/daniel/mozilla/obj-i686-pc-linux-gnu'
make: *** [build] Error 2
does anyone know how to take care of this ?

---

### Post by dbbolton on 2006-11-26
come on people. don't make me lose faith in the community.

---

### Post by dbbolton on 2006-11-26
ok. thanks so much.

---

### Post by guadafan on 2007-07-29
Had you try apt-get build-dep mozilla-firefox?

---

### Post by adamantivm on 2008-01-08
I was just able to build and run minimo under Feisty

What I did is more or less:

```

apt-get build-dep mozilla-firefox

```

as suggested by guadafan.

Then, followed [these insctuctions]("http://forums.mozillazine.org/viewtopic.php?t=552627"), which can be summarized in:

```

export CVSROOT=':pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot' 
cvs co -r MOZILLA_1_8_BRANCH mozilla/client.mk mozilla/minimo/config/ 
cp mozilla/minimo/config/mozconfig/linux_x86 mozilla/mozconfig
cd mozilla
make -f client.mk checkout
make -f client.mk build_all

```

Everything seems to be fine.

---

