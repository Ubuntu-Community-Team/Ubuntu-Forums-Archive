---
title: "Libtool version mismatch error"
date: 2010-06-09
forum: Packaging and Compiling Programs
---

### Post by arvind006 on 2010-06-09
I was installing opensrf in ubuntu 10.04
While installing I got some error message saying
libtool: Version mismatch error.  This is libtool 2.2.6 Debian-2.2.6a-4, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.6 Debian-2.2.6a-4
libtool: and run autoconf again.
make[2]: *** [libopensrf_la-osrf_message.lo] Error 63
make[2]: Leaving directory `/home/opensrf/OpenSRF-1.2.2/src/libopensrf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/opensrf/OpenSRF-1.2.2/src'
make: *** [all-recursive] Error 1

Someone please help me here.
Thanks

---

### Post by SevenMachines on 2010-06-10
have you tried autoreconf? it will rerun libtoolize 
$ autoreconf --force

---

