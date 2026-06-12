---
title: "DVDStyler ... help for compiling latest beta...."
date: 2012-04-06
forum: Packaging and Compiling Programs
---

### Post by DjDiabolik on 2012-04-06
```
diabolik@Diabolik-ubuntu:~$ cd DVD*
diabolik@Diabolik-ubuntu:~/DVDStyler-2.2b3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for install location... /usr/local
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for flex... no
checking for lex... no
checking for bison... no
checking for byacc... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for wx-config... /usr/local/bin/wx-config
checking for wxWidgets version >= 2.8.7... yes (version 2.9.3)
checking for wxWidgets static library... no
checking for wxWidgets media... yes
checking for LIBAV... yes
checking for wxSVG... yes
checking for wxSVG library with LIBAV support... yes
checking if wxWindows was linked with GTK2... yes
checking for GNOMEUI2... no
configure: WARNING: libgnomeui will not be used for rendering of thumbnails
checking for LIBEXIF... yes
checking for FONTCONFIG... yes
checking for LIBUDEV... no
configure: WARNING: libudev will not be used to get list of devices
checking for msgfmt... /usr/bin/msgfmt
checking for xmlto... no
configure: error: 
    DVDStyler requires xmlto to build DocBook documentation.
    Please check that xmlto is in path.

diabolik@Diabolik-ubuntu:~/DVDStyler-2.2b3$ 

```

I don't know.. using ubuntu 11.10 what library i again add to my sistem for compiling this programs :(
I have installed WxWidgets... WxGTK.. and other but now ??

And what i can obtain a version for reinstall in future without recompile all ?

---

### Post by oldos2er on 2012-04-06
Moved to Packaging and Compiling Programs.

---

### Post by DjDiabolik on 2012-04-07
Oh yeah.. thanks!

I thinks it this section i can obtain more support :)

I can upgrade the situation. I have resolve with xlmto.... now i need to pass/resolve this problems, I have reconfigure all with this command:

```
diabolik@Diabolik-ubuntu:~/ds-source$ ./configure --prefix=$HOME/DVDStyler --exec-prefix=$HOME/DVDStyler
```

After that i have running "make clean".... after finish again "make" and now i obtain this:
```
diabolik@Diabolik-ubuntu:~/ds-source$ ./configure --prefix=$HOME/DVDStyler --exec-prefix=$HOME/DVDStyler
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for install location... /home/diabolik/DVDStyler
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for flex... no
checking for lex... no
checking for bison... bison -y
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for wx-config... /usr/local/bin/wx-config
checking for wxWidgets version >= 2.8.7... yes (version 2.9.3)
checking for wxWidgets static library... no
checking for wxWidgets media... yes
checking for LIBAV... yes
checking for wxSVG... yes
checking for wxSVG library with LIBAV support... yes
checking if wxWindows was linked with GTK2... yes
checking for GNOMEUI2... yes
checking for LIBEXIF... yes
checking for FONTCONFIG... yes
checking for LIBUDEV... yes
checking for msgfmt... /usr/bin/msgfmt
checking for xmlto... /usr/bin/xmlto
checking for zip... /usr/bin/zip
checking for dvdauthor... /usr/bin/dvdauthor
checking for mkisofs... /usr/bin/mkisofs
checking for growisofs... /usr/bin/growisofs
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/rc/Makefile
config.status: creating wxVillaLib/Makefile
config.status: creating locale/Makefile
config.status: creating backgrounds/Makefile
config.status: creating buttons/Makefile
config.status: creating docs/Makefile
config.status: creating objects/Makefile
config.status: creating data/Makefile
config.status: creating templates/Makefile
config.status: creating src/Version.h
config.status: creating Info.plist
config.status: executing depfiles commands
diabolik@Diabolik-ubuntu:~/ds-source$ 

```

i thinks it's all ok...... after running make and this is the final output with error:
```
gcc: error: dvdvml.c: File o directory non esistente
gcc: fatal error: no input files
compilation terminated.
make[2]: *** [dvdvml.o] Errore 4
make[2]: uscita dalla directory "/home/diabolik/ds-source/src"
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory "/home/diabolik/ds-source/src"
make: *** [all-recursive] Errore 1
diabolik@Diabolik-ubuntu:~/ds-source$ 

```

Someone can help me ?

---

### Post by DjDiabolik on 2012-04-07
Installing flex from software center of ubuntu 11.10!!

Now i obtain this:
```
mediatrc_ffmpeg.cpp:30:37: fatal error: libavfilter/vsrc_buffer.h: File o directory non esistente
compilation terminated.
make[2]: *** [mediatrc_ffmpeg.o] Errore 1
make[2]: uscita dalla directory "/home/diabolik/ds-source/src"
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory "/home/diabolik/ds-source/src"
make: *** [all-recursive] Errore 1
diabolik@Diabolik-ubuntu:~/ds-source$ 

```

---

