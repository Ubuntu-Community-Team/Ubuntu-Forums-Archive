---
title: "Cross Compiling for Montavista"
date: 2008-01-22
forum: Programming Talk
---

### Post by maidentrooper on 2008-01-22
Hi, 
I am a beginner, so please bear with my question.
I made a program in C and used glade for the GUI. I am trying to cross-compile this program for MontaVista, but getting error while doing "make". 
Heres what I have been trying to do...
I first set the PATH as:
**1)**PATH=$PATH:/opt/montavista/pro/devkit/arm/xscale_le/bin/
then...
**2)**./configure CC=arm-linux-gcc CXX=arm-linux-g++ --host=arm-linux

output:
[INDENT]configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/name/program/missing: Unknown `--run' option
Try `/home/name/program/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for arm-linux-strip... arm-linux-strip
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for arm-linux-gcc... arm-linux-gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... yes
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether arm-linux-gcc accepts -g... yes
checking for arm-linux-gcc option to accept ANSI C... none needed
checking dependency style of arm-linux-gcc... gcc3
checking for strerror in -lcposix... no
checking for arm-linux-gcc... (cached) arm-linux-gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether arm-linux-gcc accepts -g... (cached) yes
checking for arm-linux-gcc option to accept ANSI C... (cached) none needed
checking dependency style of arm-linux-gcc... (cached) gcc3
checking for arm-linux-gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... arm-linux-gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... yes
checking PACKAGE_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PACKAGE_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands[/INDENT]

**3)** LDFLAGS=-L/opt/montavista/pro/devkit/arm/xscale_le/target/usr/gtk2.4-14/lib
**4)** make

The error that I get in output is :

[INDENT]arm-linux-gcc  -g -O2   -o project  main.o support.o interface.o callbacks.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    
/opt/montavista/pro/devkit/arm/xscale_le/bin/../lib/gcc-lib/armv5tel-hardhat-linux/3.3.1/../../../../armv5tel-hardhat-linux/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld returned 1 exit status
make[2]: *** [project] Error 1
make[2]: Leaving directory `/home/name/project/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/name/project'
make: *** [all] Error 2[/INDENT]

Any help is greatly appreciated 

-maidentrooper

---

### Post by WakkiTabakki on 2008-01-22
It seems to be missing the dev-file 'gtk-x11-2.0'

/N

---

### Post by maidentrooper on 2008-01-22
How do I get this file? :confused:

> **WakkiTabakki said:**
> It seems to be missing the dev-file 'gtk-x11-2.0'

/N

---

### Post by fabatera on 2009-05-08
Hi, did you find the solution for this?

---

