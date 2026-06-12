---
title: "compiling moonlight"
date: 2009-01-08
forum: Packaging and Compiling Programs
---

### Post by bardlehel on 2009-01-08
Hi, I'm trying to build mono's moonlight plugin from the source but it complains about not having the SMCS package installed.  I installed mono-smcs package but the configure script didn't recognize it.  I'm wondering what exact package i need to be able to compile.

checking for FFMPEG... yes
checking libavcodec/avcodec.h usability... no
checking libavcodec/avcodec.h presence... no
checking for libavcodec/avcodec.h... no
checking for MONO... yes
checking for SMCS... configure: error: Package requirements (smcs) were not met:

No package 'smcs' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SMCS_CFLAGS
and SMCS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by directhex on 2009-01-08
2.0 support isn't remotely complete enough yet to warrant turning it on. Don't bother using --with-managed. It's probably moaning because you need a much newer smcs than you have installed, e.g. 2.2 or trunk

---

