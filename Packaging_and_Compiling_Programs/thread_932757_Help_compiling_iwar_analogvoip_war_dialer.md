---
title: "Help compiling iwar analog/voip war dialer"
date: 2008-09-28
forum: Packaging and Compiling Programs
---

### Post by ccrape on 2008-09-28
I was able to compile iwar with postgres support but during the "make" process I get the following error.  I'm running ubuntu-eee on a Asus 900 with 2gb ram if that helps.  Any assistance would be greatly appreciated.

make  all-am
make[1]: Entering directory `/home/***/iwar'
if gcc -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/include/postgresql -D_POSIX -g -O2 -MT iwar-engine.o -MD -MP -MF ".deps/iwar-engine.Tpo" -c -o iwar-engine.o iwar-engine.c; \
	then mv -f ".deps/iwar-engine.Tpo" ".deps/iwar-engine.Po"; else rm -f ".deps/iwar-engine.Tpo"; exit 1; fi
iwar-engine.c: In function ‘main’:
iwar-engine.c:2187: error: too few arguments to function ‘iaxc_initialize’
make[1]: *** [iwar-engine.o] Error 1
make[1]: Leaving directory `/home/***/iwar'
make: *** [all] Error 2

---

### Post by komputes on 2011-02-23
The iaxc_initialize build error is covered in this thread:
[http://ubuntuforums.org/showthread.php?t=1693836](http://ubuntuforums.org/showthread.php?t=1693836)

---

