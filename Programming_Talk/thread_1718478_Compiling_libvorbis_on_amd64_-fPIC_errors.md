---
title: "Compiling libvorbis on amd64: -fPIC errors"
date: 2011-03-31
forum: Programming Talk
---

### Post by markdavidoff on 2011-03-31
I am trying to compile the latest audacity source code on amd64 ubuntu desktop 10.10, and I am running into a (probably simple) issue I don't know how to resolve.

I could just install libvorbis-dev, and the configure tool will use it (this results in a build success), but I want to be able to modify the vorbis library and see how it affects my vorbis files in audacity for research purposes.

```
make[5]: Entering directory `/home/mark/audacity/audacity-read-only/lib-src/libvorbis/lib'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O20 -ffast-math -D_REENTRANT -fsigned-char  -DUSE_MEMORY_H -no-undefined -version-info 4:0:4  -o libvorbis.la -rpath /usr/local/lib mdct.lo smallft.lo block.lo envelope.lo window.lo lsp.lo lpc.lo analysis.lo synthesis.lo psy.lo info.lo floor1.lo floor0.lo res0.lo mapping0.lo registry.lo codebook.lo sharedbook.lo lookup.lo bitrate.lo -L../.. -logg -lm -L../.. -logg
gcc -shared  .libs/mdct.o .libs/smallft.o .libs/block.o .libs/envelope.o .libs/window.o .libs/lsp.o .libs/lpc.o .libs/analysis.o .libs/synthesis.o .libs/psy.o .libs/info.o .libs/floor1.o .libs/floor0.o .libs/res0.o .libs/mapping0.o .libs/registry.o .libs/codebook.o .libs/sharedbook.o .libs/lookup.o .libs/bitrate.o  -L/home/mark/audacity/audacity-read-only/lib-src -lm -logg  -Wl,-soname -Wl,libvorbis.so.0 -o .libs/libvorbis.so.0.4.0
/usr/bin/ld: /home/mark/audacity/audacity-read-only/lib-src/libogg.a(bitwise.o): relocation R_X86_64_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/home/mark/audacity/audacity-read-only/lib-src/libogg.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[5]: *** [libvorbis.la] Error 1
make[5]: Leaving directory `/home/mark/audacity/audacity-read-only/lib-src/libvorbis/lib'

```

I can't seem to "recompile with -fPIC" maybe I'm doing something wrong...I just added -fPIC to the CFLAGS and CPPFLAGS environment variables, and that did nothing. I also tried running

```
gcc -shared **-fPIC**  .libs/mdct.o .libs/smallft.o .libs/block.o .libs/envelope.o .libs/window.o .libs/lsp.o .libs/lpc.o .libs/analysis.o .libs/synthesis.o .libs/psy.o .libs/info.o .libs/floor1.o .libs/floor0.o .libs/res0.o .libs/mapping0.o .libs/registry.o .libs/codebook.o .libs/sharedbook.o .libs/lookup.o .libs/bitrate.o  -L/home/mark/audacity/audacity-read-only/lib-src -lm -logg  -Wl,-soname -Wl,libvorbis.so.0 -o .libs/libvorbis.so.0.4.0

```

but got the same result.

---

### Post by MadCow108 on 2011-03-31
you have to compile /home/mark/audacity/audacity-read-only/lib-src/libogg.a with -fPIC

---

### Post by markdavidoff on 2011-04-01
Lol...I was trying to recompile bitwise.o
Thanks

---

