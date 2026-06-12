---
title: "[SOLVED] Compiling XaraLX on Intrepid"
date: 2009-01-02
forum: Packaging and Compiling Programs
---

### Post by lwhitmore on 2009-01-02
Hi

I'm having problems compiling XaraLX on Intrepid.  I'm not very experienced at compiling programs - would appreciate any advice.

I've managed to get the ./configure script to parse without any errors, output follows:...

```
 
./configure --enable-debug --enable-unicode
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for pkg-config... /usr/bin/pkg-config
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for /proc/self/maps... yes
checking whether everything is installed to the same prefix... yes
checking whether binary relocation support should be enabled... yes
checking for pthread_getspecific in -lpthread... yes
checking whether binary relocation should use threads... yes
checking Automake (1.9.6)... Version OK
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking Compiler... gcc >= 3.4.0, PreCompiled headers enabled
checking for ranlib... ranlib
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for void*... yes
checking size of void*... 4
checking for long long... yes
checking size of long long... 8
checking for long... yes
checking size of long... 4
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for __int64... no
checking size of __int64... 0
checking wxWidgets version... 2.6.3
checking wxWidgets GTK usage... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking wxWidgets wxrc utility... found
checking libxml2 version... 2.6.32
checking freetype version... 9.18.3
checking for PANGOX... yes
checking Linker... GNU ld
checking CDraw location... libs/x86
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
configure: creating ./config.status
config.status: creating Makefile
config.status: creating PreComp/Makefile
config.status: creating Kernel/Makefile
config.status: creating wxOil/Makefile
config.status: creating tools/Makefile
config.status: creating wxXtra/Makefile
config.status: creating xarlib/Makefile
config.status: creating xarlib/Xar.pc
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile

```

The last lines of output after running 'make' are....

```
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"XaraLX\" -DVERSION=\"0.7\" -DENABLE_BINRELOC= -DHAVE_LIBPTHREAD=1 -DBR_PTHREAD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_VOIDP=4 -DSIZEOF_LONG_LONG=8 -DSIZEOF_LONG=4 -DSIZEOF_INT=4 -DSIZEOF_SHORT=2 -DSIZEOF___INT64=0 -DENABLE_NLS=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1  -I. -I.    -Wall -Wno-unknown-pragmas -g -fexceptions -O0 -fno-strict-aliasing  -Wstrict-aliasing=2 -ggdb -D_DEBUG -I/usr/lib/wx/include/gtk2-unicode-debug-2.6 -I/usr/include/wx-2.6 -D__WXDEBUG__ -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/libxml2  -I../PreComp -I../wxOil -I.././Kernel -I.././wxOil -I.././wxOil/Res -I.././tools -I.././GDraw -I.././PreComp -I.././wxXtra -DUSE_NATIVE_XLONG -DBUILDSHADOWS -DOLD_MATRIX_TRANSFORMATIONS -DVECTOR_STROKING -DEXCLUDE_FROM_XARALX -DNEW_SHADOW_RENDER -DNO_XARACMS -DNEW_FEATURES -DSHOWPORTNOTE -DDO_EXPORT  -MT libwxOil_a-ppmfiltr.o -MD -MP -MF ".deps/libwxOil_a-ppmfiltr.Tpo" -c -o libwxOil_a-ppmfiltr.o `test -f 'ppmfiltr.cpp' || echo './'`ppmfiltr.cpp; \
	then mv -f ".deps/libwxOil_a-ppmfiltr.Tpo" ".deps/libwxOil_a-ppmfiltr.Po"; else rm -f ".deps/libwxOil_a-ppmfiltr.Tpo"; exit 1; fi
In file included from ppmfiltr.cpp:108:
.././Kernel/nodebmp.h: In member function ‘virtual TCHAR* NodeBitmap::GetDefaultOpToken()’:
.././Kernel/nodebmp.h:206: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp: At global scope:
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp:152: warning: deprecated conversion from string constant to ‘TCHAR*’
ppmfiltr.cpp: In member function ‘BOOL BasePMFilter::ReadFromFile(CCLexFile*, BITMAPINFO**, BYTE**, String_64*)’:
ppmfiltr.cpp:789: warning: deprecated conversion from string constant to ‘char*’
ppmfiltr.cpp:791: warning: deprecated conversion from string constant to ‘char*’
ppmfiltr.cpp:792: warning: deprecated conversion from string constant to ‘char*’
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"XaraLX\" -DVERSION=\"0.7\" -DENABLE_BINRELOC= -DHAVE_LIBPTHREAD=1 -DBR_PTHREAD=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_VOIDP=4 -DSIZEOF_LONG_LONG=8 -DSIZEOF_LONG=4 -DSIZEOF_INT=4 -DSIZEOF_SHORT=2 -DSIZEOF___INT64=0 -DENABLE_NLS=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1  -I. -I.    -Wall -Wno-unknown-pragmas -g -fexceptions -O0 -fno-strict-aliasing  -Wstrict-aliasing=2 -ggdb -D_DEBUG -I/usr/lib/wx/include/gtk2-unicode-debug-2.6 -I/usr/include/wx-2.6 -D__WXDEBUG__ -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/libxml2  -I../PreComp -I../wxOil -I.././Kernel -I.././wxOil -I.././wxOil/Res -I.././tools -I.././GDraw -I.././PreComp -I.././wxXtra -DUSE_NATIVE_XLONG -DBUILDSHADOWS -DOLD_MATRIX_TRANSFORMATIONS -DVECTOR_STROKING -DEXCLUDE_FROM_XARALX -DNEW_SHADOW_RENDER -DNO_XARACMS -DNEW_FEATURES -DSHOWPORTNOTE -DDO_EXPORT  -MT libwxOil_a-bitmapgriddropdown.o -MD -MP -MF ".deps/libwxOil_a-bitmapgriddropdown.Tpo" -c -o libwxOil_a-bitmapgriddropdown.o `test -f 'bitmapgriddropdown.cpp' || echo './'`bitmapgriddropdown.cpp; \
	then mv -f ".deps/libwxOil_a-bitmapgriddropdown.Tpo" ".deps/libwxOil_a-bitmapgriddropdown.Po"; else rm -f ".deps/libwxOil_a-bitmapgriddropdown.Tpo"; exit 1; fi
bitmapgriddropdown.cpp: In member function ‘wxBitmap* CBGDDCachedItem::GetWxBitmap(wxSize) const’:
bitmapgriddropdown.cpp:299: error: ‘find_if’ was not declared in this scope
make[2]: *** [libwxOil_a-bitmapgriddropdown.o] Error 1
make[2]: Leaving directory `/home/luke/Documents/CODE/xaraLX_new/XaraLX-0.7r1785/wxOil'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/luke/Documents/CODE/xaraLX_new/XaraLX-0.7r1785/wxOil'
make: *** [all-recursive] Error 1

```

I initially tried to compile this using wxwidgets v.2.8, and downgraded to 2.6 as I thought this might be causing the error.  I also had a go at setting the gcc compiler to use v3.4 rather than v4.

If you could help me decode the make errors, and point me in the right direction, I'd be really grateful :confused:

---

### Post by lwhitmore on 2009-01-02
Figured out the problem after a lot of red herrings....

Apparently something changed in a new version of the compiler, which means that the <algorithm> library needs to be manually included.

```
bitmapgriddropdown.cpp:299: error: &#8216;find_if&#8217; was not declared in this scope

```

... find_if is part of the <algorithm> library.

So I just added ```
#include <algorithm>
```

to the includes section in bitmapgriddropdown.cpp and voila... it compiled.

I also found out that FTBFS is a relevant acronym = fails to build from source.

---

### Post by babuz' on 2009-04-30
Thanks a lot! Your tip worked like a charm (Fedora Core 10 64bit)

---

