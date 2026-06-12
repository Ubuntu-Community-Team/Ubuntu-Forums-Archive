---
title: "Using checkinstall to make a .deb"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by rogerdean on 2008-09-26
Hello folks

I'm trying to make a .deb of Sunbird 0.9 using checkinstall and the instructions here...

[http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

I think I need some extra packages installed which are not mentioned in the thread. One I'm sure is build-essential - can anyone tell me what else I'll need? The error message I'm getting at the moment ends with...

checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
roger@roger-laptop:~/mozilla$ 

Any advice appreciated!
Cheers
Roger

---

### Post by Cypher on 2008-09-26
Strat with these
```

sudo apt-get install libgtk2.0-0 libgtk2.0-dev

```

---

### Post by rogerdean on 2008-09-26
Thanks very much Cypher, I'm now getting a few more steps through the process. Readout now ends with this error...

checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: error: --enable-application=APP is required

What's next??
Cheers
Roger

---

### Post by xeth_delta on 2008-09-26
> **rogerdean said:**
> Thanks very much Cypher, I'm now getting a few more steps through the process. Readout now ends with this error...

checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
configure: error: --enable-application=APP is required

What's next??
Cheers
Roger

These errors appear when running the configure script before compilation, I would presume, this is before compilation and deb creation.

Run the following
```
./configure --help
```
There will be a lot of information there, look for the line with "--enable-application..." and see what it is about and what it requires. I would guess it expects an application name in there.
Let us know how it goes.

---

### Post by rogerdean on 2008-09-26
Thanks xeth_delta

Right, good advice re the --help. That told me that the command I needed for Sunbird was ./configure --enable-application=calendar

The additional packages I found I needed from the start, by the way, were build-essential libgtk2.0-0 libgtk2.0-dev libidl-dev

```
roger@roger-laptop:~/mozilla$ ./configure --enable-application=calendar
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for nsinstall... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking for as... /usr/bin/as
checking for ar... ar
checking for ld... ld
checking for strip... strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for minimum required perl version >= 5.004... 5.008008
checking for full perl installation... yes
checking for doxygen... :
checking for whoami... /usr/bin/whoami
checking for autoconf... :
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for makedepend... /usr/bin/makedepend
checking for xargs... /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... no
checking whether ld has archive extraction flags... yes
checking that static assertion macros used in autoconf tests work... yes
checking for 64-bit OS... no
checking for ANSI C header files... yes
checking for working const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for st_blksize in struct stat... yes
checking for siginfo_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for int64... no
checking for uint... yes
checking for uint_t... no
checking for uint16_t... no
checking for uname.domainname... yes
checking for uname.__domainname... no
checking for usable wchar_t (2 bytes, unsigned)... no
checking for compiler -fshort-wchar option... yes
checking for visibility(hidden) attribute... yes
checking for visibility(default) attribute... yes
checking for visibility pragma support... yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for sys/byteorder.h... no
checking for compat.h... no
checking for getopt.h... yes
checking for sys/bitypes.h... yes
checking for memory.h... yes
checking for unistd.h... yes
checking for gnu/libc-version.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for X11/XKBlib.h... yes
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... no
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking for socket in -lsocket... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... no
checking for 8-bit clean memcmp... yes
checking for random... yes
checking for strerror... yes
checking for lchown... yes
checking for fchmod... yes
checking for snprintf... yes
checking for statvfs... yes
checking for memmove... yes
checking for rint... yes
checking for stat64... yes
checking for lstat64... yes
checking for flockfile... yes
checking for getpagesize... yes
checking for localtime_r... yes
checking for strtok_r... yes
checking for wcrtomb... yes
checking for mbrtowc... yes
checking for res_ninit()... yes
checking for gnu_get_libc_version()... yes
checking for iconv in -lc... yes
checking for iconv()... yes
checking for iconv() with const input... no
checking for nl_langinfo and CODESET... yes
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... yes
checking for C++ exceptions flag... -fno-exceptions
checking for gcc 3.0 ABI... yes
checking for C++ "explicit" keyword... yes
checking for C++ "typename" keyword... yes
checking for modern C++ template specialization syntax support... yes
checking whether partial template specialization works... yes
checking whether operators must be re-defined for templates derived from templates... no
checking whether we need to cast a derived template to pass as its base class... no
checking whether the compiler can resolve const ambiguities for templates... yes
checking whether the C++ "using" keyword can change access... yes
checking whether the C++ "using" keyword resolves ambiguity... yes
checking for "std::" namespace... yes
checking whether standard template operator!=() is ambiguous... unambiguous
checking for C++ reinterpret_cast... yes
checking for C++ dynamic_cast to void*... yes
checking whether C++ requires implementation of unused virtual methods... yes
checking for trouble comparing to zero near std::operator!=()... no
checking for LC_MESSAGES... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 1.3.7... yes
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for xft... yes
checking MOZ_XFT_CFLAGS... -I/usr/include/freetype2  
checking MOZ_XFT_LIBS...   -lXft -lfontconfig  
checking for pango >= 1.1.0... yes
checking _PANGOCHK_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS...   -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for XpGetPrinterList in -lXp... no
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... checking for gconf-2.0 >= 1.2.1... checking for libgnome-2.0 >= 2.0... checking for libgnomeui-2.0 >= 2.2.0... checking for valid optimization flags... yes
checking for __builtin_vec_new... no
checking for __builtin_vec_delete... no
checking for __builtin_new... no
checking for __builtin_delete... no
checking for __pure_virtual... no
checking for __cxa_demangle... yes
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking whether compiler supports -Wno-long-long... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0... yes
checking LIBIDL_CFLAGS... -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking LIBIDL_LIBS...   -lIDL-2 -lglib-2.0  
checking for glib-2.0 >= 1.3.7... yes
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS...   -lglib-2.0  
checking for stdint.h... yes
checking for inttypes.h... yes
checking for sys/int_types.h... no
creating mozilla-config.h
==== mozilla-config.h =================================
/* List of defines generated by configure. Included with preprocessor flag,
 * -include, to avoid long list of -D defines on the compile command-line.
 * Do not edit.
 */

#ifndef _MOZILLA_CONFIG_H_
#define _MOZILLA_CONFIG_H_

#define ACCESSIBILITY 1
#define D_INO d_ino
#define HAVE_DIRENT_H 1
#define HAVE_FCHMOD 1
#define HAVE_FLOCKFILE 1
#define HAVE_GETOPT_H 1
#define HAVE_GNU_GET_LIBC_VERSION 1
#define HAVE_GNU_LIBC_VERSION_H 1
#define HAVE_I18N_LC_MESSAGES 1
#define HAVE_INT16_T 1
#define HAVE_INT32_T 1
#define HAVE_INT64_T 1
#define HAVE_INTTYPES_H 1
#define HAVE_LANGINFO_CODESET 1
#define HAVE_LCHOWN 1
#define HAVE_LIBDL 1
#define HAVE_LIBM 1
#define HAVE_LOCALTIME_R 1
#define HAVE_LSTAT64 1
#define HAVE_MALLOC_H 1
#define HAVE_MEMMOVE 1
#define HAVE_MEMORY_H 1
#define HAVE_NL_TYPES_H 1
#define HAVE_RANDOM 1
#define HAVE_RES_NINIT 1
#define HAVE_RINT 1
#define HAVE_SIGINFO_T 1
#define HAVE_SNPRINTF 1
#define HAVE_STAT64 1
#define HAVE_STDINT_H 1
#define HAVE_STRERROR 1
#define HAVE_STRTOK_R 1
#define HAVE_ST_BLKSIZE 1
#define HAVE_SYS_BITYPES_H 1
#define HAVE_SYS_CDEFS_H 1
#define HAVE_SYS_STATFS_H 1
#define HAVE_SYS_STATVFS_H 1
#define HAVE_UINT 1
#define HAVE_UINT64_T 1
#define HAVE_UNAME_DOMAINNAME_FIELD 1
#define HAVE_UNISTD_H 1
#define HAVE_VA_COPY 1
#define HAVE_VISIBILITY_ATTRIBUTE 1
#define HAVE_VISIBILITY_HIDDEN_ATTRIBUTE 1
#define HAVE_X11_XKBLIB_H 1
#define HAVE___CXA_DEMANGLE 1
#define IBMBIDI 1
#define JS_THREADSAFE 1
#define MOZILLA_1_8_BRANCH 1
#define MOZILLA_LOCALE_VERSION "1.8.1"
#define MOZILLA_REGION_VERSION "1.8.1"
#define MOZILLA_SKIN_VERSION "1.8"
#define MOZILLA_VERSION "1.8.1.18pre"
#define MOZILLA_VERSION_U 1.8.1.18pre
#define MOZ_ACCESSIBILITY_ATK 1
#define MOZ_BUILD_APP calendar
#define MOZ_DEFAULT_TOOLKIT "gtk2"
#define MOZ_DISTRIBUTION_ID "org.mozilla"
#define MOZ_DLL_SUFFIX ".so"
#define MOZ_ENABLE_CANVAS 1
#define MOZ_ENABLE_OLD_ABI_COMPAT_WRAPPERS 1
#define MOZ_ENABLE_XFT 1
#define MOZ_ENABLE_XREMOTE 1
#define MOZ_FEEDS 1
#define MOZ_JSLOADER 1
#define MOZ_LOGGING 1
#define MOZ_MORK 1
#define MOZ_PROFILELOCKING 1
#define MOZ_STORAGE 1
#define MOZ_SUNBIRD 1
#define MOZ_UPDATE_CHANNEL default
#define MOZ_USER_DIR ".mozilla"
#define MOZ_VIEW_SOURCE 1
#define MOZ_WIDGET_GTK2 1
#define MOZ_X11 1
#define MOZ_XPINSTALL 1
#define MOZ_XTF 1
#define MOZ_XUL 1
#define MOZ_XUL_APP 1
#define NO_X11 1
#define NS_PRINTING 1
#define NS_PRINT_PREVIEW 1
#define STDC_HEADERS 1
#define UNIX_ASYNC_DNS 1
#define VA_COPY va_copy
#define XP_UNIX 1
#define X_DISPLAY_MISSING 1
#define _REENTRANT 1

#endif /* _MOZILLA_CONFIG_H_ */

creating Makefile
creating build/Makefile
creating build/unix/Makefile
creating config/Makefile
creating config/mkdepend/Makefile
creating caps/Makefile
creating caps/idl/Makefile
creating caps/include/Makefile
creating caps/src/Makefile
creating chrome/Makefile
creating chrome/public/Makefile
creating chrome/src/Makefile
creating embedding/minimo/chromelite/Makefile
creating rdf/chrome/Makefile
creating rdf/chrome/public/Makefile
creating rdf/chrome/build/Makefile
creating rdf/chrome/src/Makefile
creating rdf/chrome/tools/Makefile
creating rdf/chrome/tools/chromereg/Makefile
creating db/Makefile
creating db/mdb/Makefile
creating db/mdb/public/Makefile
creating db/mork/Makefile
creating db/mork/build/Makefile
creating db/mork/src/Makefile
creating dbm/Makefile
creating dbm/include/Makefile
creating dbm/src/Makefile
creating dbm/tests/Makefile
creating docshell/Makefile
creating docshell/base/Makefile
creating docshell/build/Makefile
creating dom/Makefile
creating dom/public/Makefile
creating dom/public/base/Makefile
creating dom/public/coreEvents/Makefile
creating dom/public/idl/Makefile
creating dom/public/idl/base/Makefile
creating dom/public/idl/canvas/Makefile
creating dom/public/idl/core/Makefile
creating dom/public/idl/css/Makefile
creating dom/public/idl/events/Makefile
creating dom/public/idl/html/Makefile
creating dom/public/idl/range/Makefile
creating dom/public/idl/stylesheets/Makefile
creating dom/public/idl/views/Makefile
creating dom/public/idl/xbl/Makefile
creating dom/public/idl/xpath/Makefile
creating dom/public/idl/xul/Makefile
creating dom/src/Makefile
creating dom/src/base/Makefile
creating dom/src/events/Makefile
creating dom/src/jsurl/Makefile
creating dom/locales/Makefile
creating editor/Makefile
creating editor/public/Makefile
creating editor/idl/Makefile
creating editor/txmgr/Makefile
creating editor/txmgr/idl/Makefile
creating editor/txmgr/public/Makefile
creating editor/txmgr/src/Makefile
creating editor/txmgr/tests/Makefile
creating editor/txtsvc/Makefile
creating editor/txtsvc/public/Makefile
creating editor/txtsvc/src/Makefile
creating embedding/Makefile
creating embedding/base/Makefile
creating embedding/browser/Makefile
creating embedding/browser/activex/src/Makefile
creating embedding/browser/activex/src/control/Makefile
creating embedding/browser/activex/src/control_kicker/Makefile
creating embedding/browser/build/Makefile
creating embedding/browser/chrome/Makefile
creating embedding/browser/webBrowser/Makefile
creating embedding/browser/gtk/Makefile
creating embedding/browser/gtk/src/Makefile
creating embedding/browser/gtk/tests/Makefile
creating embedding/browser/qt/Makefile
creating embedding/browser/qt/src/Makefile
creating embedding/browser/qt/tests/Makefile
creating embedding/browser/photon/Makefile
creating embedding/browser/photon/src/Makefile
creating embedding/browser/photon/tests/Makefile
creating embedding/browser/cocoa/Makefile
creating embedding/components/Makefile
creating embedding/components/build/Makefile
creating embedding/components/windowwatcher/Makefile
creating embedding/components/windowwatcher/public/Makefile
creating embedding/components/windowwatcher/src/Makefile
creating embedding/components/ui/Makefile
creating embedding/components/ui/helperAppDlg/Makefile
creating embedding/components/ui/progressDlg/Makefile
creating embedding/config/Makefile
creating embedding/tests/Makefile
creating embedding/tests/cocoaEmbed/Makefile
creating embedding/tests/winEmbed/Makefile
creating embedding/tests/mfcembed/Makefile
creating embedding/tests/mfcembed/components/Makefile
creating parser/expat/Makefile
creating parser/expat/lib/Makefile
creating extensions/Makefile
creating extensions/xmlextras/Makefile
creating extensions/xmlextras/pointers/Makefile
creating extensions/xmlextras/pointers/src/Makefile
creating extensions/xmlextras/build/Makefile
creating extensions/xmlextras/build/src/Makefile
creating extensions/transformiix/source/base/Makefile
creating extensions/transformiix/source/main/Makefile
creating extensions/transformiix/source/xml/dom/standalone/Makefile
creating extensions/transformiix/source/xml/dom/Makefile
creating extensions/transformiix/source/xml/parser/Makefile
creating extensions/transformiix/source/xml/Makefile
creating extensions/transformiix/source/xpath/Makefile
creating extensions/transformiix/source/xslt/functions/Makefile
creating extensions/transformiix/source/xslt/util/Makefile
creating extensions/transformiix/source/xslt/Makefile
creating extensions/transformiix/source/Makefile
creating extensions/transformiix/Makefile
creating extensions/transformiix/resources/Makefile
creating gc/boehm/Makefile
creating gc/boehm/leaksoup/Makefile
creating gfx/Makefile
creating gfx/idl/Makefile
creating gfx/public/Makefile
creating gfx/src/Makefile
creating gfx/src/beos/Makefile
creating gfx/src/gtk/Makefile
creating gfx/src/ps/Makefile
creating gfx/src/psshared/Makefile
creating gfx/src/photon/Makefile
creating gfx/src/mac/Makefile
creating gfx/src/qt/Makefile
creating gfx/src/xlib/Makefile
creating gfx/src/os2/Makefile
creating gfx/src/xlibrgb/Makefile
creating gfx/src/windows/Makefile
creating gfx/src/cairo/Makefile
creating gfx/tests/Makefile
creating gfx/cairo/Makefile
creating gfx/cairo/libpixman/src/Makefile
creating gfx/cairo/cairo/src/Makefile
creating accessible/Makefile
creating accessible/public/Makefile
creating accessible/public/msaa/Makefile
creating accessible/src/Makefile
creating accessible/src/base/Makefile
creating accessible/src/html/Makefile
creating accessible/src/xul/Makefile
creating accessible/src/msaa/Makefile
creating accessible/src/atk/Makefile
creating accessible/src/mac/Makefile
creating accessible/build/Makefile
creating parser/htmlparser/Makefile
creating parser/htmlparser/robot/Makefile
creating parser/htmlparser/robot/test/Makefile
creating parser/htmlparser/public/Makefile
creating parser/htmlparser/src/Makefile
creating parser/htmlparser/tests/Makefile
creating parser/htmlparser/tests/grabpage/Makefile
creating parser/htmlparser/tests/logparse/Makefile
creating parser/htmlparser/tests/html/Makefile
creating parser/htmlparser/tests/outsinks/Makefile
creating intl/Makefile
creating intl/chardet/Makefile
creating intl/chardet/public/Makefile
creating intl/chardet/src/Makefile
creating intl/uconv/Makefile
creating intl/uconv/idl/Makefile
creating intl/uconv/public/Makefile
creating intl/uconv/src/Makefile
creating intl/uconv/tests/Makefile
creating intl/uconv/ucvja/Makefile
creating intl/uconv/ucvlatin/Makefile
creating intl/uconv/ucvcn/Makefile
creating intl/uconv/ucvtw/Makefile
creating intl/uconv/ucvtw2/Makefile
creating intl/uconv/ucvko/Makefile
creating intl/uconv/ucvibm/Makefile
creating intl/uconv/native/Makefile
creating intl/locale/Makefile
creating intl/locale/public/Makefile
creating intl/locale/idl/Makefile
creating intl/locale/src/Makefile
creating intl/locale/src/unix/Makefile
creating intl/locale/src/os2/Makefile
creating intl/locale/src/windows/Makefile
creating intl/locale/tests/Makefile
creating intl/lwbrk/Makefile
creating intl/lwbrk/src/Makefile
creating intl/lwbrk/public/Makefile
creating intl/lwbrk/tests/Makefile
creating intl/unicharutil/Makefile
creating intl/unicharutil/idl/Makefile
creating intl/unicharutil/src/Makefile
creating intl/unicharutil/public/Makefile
creating intl/unicharutil/tables/Makefile
creating intl/unicharutil/tests/Makefile
creating intl/unicharutil/tools/Makefile
creating intl/strres/Makefile
creating intl/strres/public/Makefile
creating intl/strres/src/Makefile
creating intl/strres/tests/Makefile
creating jpeg/Makefile
creating js/Makefile
creating js/src/Makefile
creating js/src/fdlibm/Makefile
creating js/jsd/Makefile
creating js/jsd/idl/Makefile
creating content/Makefile
creating content/base/Makefile
creating content/base/public/Makefile
creating content/base/src/Makefile
creating content/canvas/Makefile
creating content/canvas/public/Makefile
creating content/canvas/src/Makefile
creating content/events/Makefile
creating content/events/public/Makefile
creating content/events/src/Makefile
creating content/html/Makefile
creating content/html/content/Makefile
creating content/html/content/public/Makefile
creating content/html/content/src/Makefile
creating content/html/document/Makefile
creating content/html/document/public/Makefile
creating content/html/document/src/Makefile
creating content/xml/Makefile
creating content/xml/content/Makefile
creating content/xml/content/public/Makefile
creating content/xml/content/src/Makefile
creating content/xml/document/Makefile
creating content/xml/document/public/Makefile
creating content/xml/document/src/Makefile
creating content/xul/Makefile
creating content/xul/content/Makefile
creating content/xul/content/public/Makefile
creating content/xul/content/src/Makefile
creating content/xul/document/Makefile
creating content/xul/document/public/Makefile
creating content/xul/document/src/Makefile
creating content/xul/templates/public/Makefile
creating content/xul/templates/src/Makefile
creating content/xbl/Makefile
creating content/xbl/public/Makefile
creating content/xbl/src/Makefile
creating content/xbl/builtin/Makefile
creating content/xsl/Makefile
creating content/xsl/public/Makefile
creating content/xtf/Makefile
creating content/xtf/public/Makefile
creating content/xtf/src/Makefile
creating layout/Makefile
creating layout/base/Makefile
creating layout/base/tests/Makefile
creating layout/build/Makefile
creating layout/forms/Makefile
creating layout/html/tests/Makefile
creating layout/style/Makefile
creating layout/printing/Makefile
creating layout/tools/Makefile
creating layout/xul/Makefile
creating layout/xul/base/Makefile
creating layout/xul/base/public/Makefile
creating layout/xul/base/src/Makefile
creating layout/xul/base/src/tree/Makefile
creating layout/xul/base/src/tree/src/Makefile
creating layout/xul/base/src/tree/public/Makefile
creating layout/xtf/Makefile
creating layout/xtf/src/Makefile
creating modules/libreg/Makefile
creating modules/libreg/include/Makefile
creating modules/libreg/src/Makefile
creating modules/libreg/standalone/Makefile
creating modules/libimg/Makefile
creating modules/libimg/png/Makefile
creating modules/libpr0n/Makefile
creating modules/libpr0n/public/Makefile
creating modules/libpr0n/src/Makefile
creating modules/libpr0n/decoders/Makefile
creating modules/libpr0n/decoders/gif/Makefile
creating modules/libpr0n/decoders/png/Makefile
creating modules/libpr0n/decoders/jpeg/Makefile
creating modules/libpr0n/decoders/bmp/Makefile
creating modules/libpr0n/decoders/icon/Makefile
creating modules/libpr0n/decoders/icon/win/Makefile
creating modules/libpr0n/decoders/icon/gtk/Makefile
creating modules/libpr0n/decoders/icon/beos/Makefile
creating modules/libpr0n/decoders/xbm/Makefile
creating modules/libjar/Makefile
creating modules/libjar/standalone/Makefile
creating modules/libpref/Makefile
creating modules/libpref/public/Makefile
creating modules/libpref/src/Makefile
creating modules/libutil/Makefile
creating modules/libutil/public/Makefile
creating modules/libutil/src/Makefile
creating js/src/liveconnect/Makefile
creating js/src/liveconnect/classes/Makefile
creating modules/oji/Makefile
creating modules/oji/public/Makefile
creating modules/oji/src/Makefile
creating plugin/oji/JEP/Makefile
creating modules/plugin/Makefile
creating modules/plugin/base/src/Makefile
creating modules/plugin/base/public/Makefile
creating modules/plugin/samples/simple/Makefile
creating modules/plugin/samples/SanePlugin/Makefile
creating modules/plugin/samples/default/unix/Makefile
creating modules/plugin/tools/sdk/Makefile
creating modules/plugin/tools/sdk/samples/Makefile
creating modules/plugin/tools/sdk/samples/common/Makefile
creating modules/plugin/tools/sdk/samples/basic/windows/Makefile
creating modules/plugin/tools/sdk/samples/scriptable/windows/Makefile
creating modules/plugin/tools/sdk/samples/simple/Makefile
creating modules/plugin/tools/sdk/samples/winless/windows/Makefile
creating netwerk/Makefile
creating netwerk/base/Makefile
creating netwerk/base/public/Makefile
creating netwerk/base/src/Makefile
creating netwerk/build/Makefile
creating netwerk/build2/Makefile
creating netwerk/cache/Makefile
creating netwerk/cache/public/Makefile
creating netwerk/cache/src/Makefile
creating netwerk/cookie/Makefile
creating netwerk/cookie/public/Makefile
creating netwerk/cookie/src/Makefile
creating netwerk/dns/Makefile
creating netwerk/dns/public/Makefile
creating netwerk/dns/src/Makefile
creating netwerk/protocol/Makefile
creating netwerk/protocol/about/Makefile
creating netwerk/protocol/about/public/Makefile
creating netwerk/protocol/about/src/Makefile
creating netwerk/protocol/data/Makefile
creating netwerk/protocol/data/public/Makefile
creating netwerk/protocol/data/src/Makefile
creating netwerk/protocol/file/Makefile
creating netwerk/protocol/file/public/Makefile
creating netwerk/protocol/file/src/Makefile
creating netwerk/protocol/ftp/Makefile
creating netwerk/protocol/ftp/public/Makefile
creating netwerk/protocol/ftp/src/Makefile
creating netwerk/protocol/gopher/Makefile
creating netwerk/protocol/gopher/src/Makefile
creating netwerk/protocol/http/Makefile
creating netwerk/protocol/http/public/Makefile
creating netwerk/protocol/http/src/Makefile
creating netwerk/protocol/res/Makefile
creating netwerk/protocol/res/public/Makefile
creating netwerk/protocol/res/src/Makefile
creating netwerk/mime/Makefile
creating netwerk/mime/public/Makefile
creating netwerk/mime/src/Makefile
creating netwerk/socket/Makefile
creating netwerk/socket/base/Makefile
creating netwerk/streamconv/Makefile
creating netwerk/streamconv/converters/Makefile
creating netwerk/streamconv/public/Makefile
creating netwerk/streamconv/src/Makefile
creating netwerk/streamconv/test/Makefile
creating netwerk/test/Makefile
creating netwerk/testserver/Makefile
creating netwerk/resources/Makefile
creating netwerk/locales/Makefile
creating netwerk/system/Makefile
creating netwerk/system/win32/Makefile
creating uriloader/exthandler/Makefile
creating profile/Makefile
creating profile/src/Makefile
creating profile/public/Makefile
creating profile/resources/Makefile
creating profile/pref-migrator/Makefile
creating profile/pref-migrator/public/Makefile
creating profile/pref-migrator/src/Makefile
creating profile/pref-migrator/resources/Makefile
creating profile/defaults/Makefile
creating profile/dirserviceprovider/Makefile
creating profile/dirserviceprovider/public/Makefile
creating profile/dirserviceprovider/src/Makefile
creating rdf/Makefile
creating rdf/base/Makefile
creating rdf/base/idl/Makefile
creating rdf/base/public/Makefile
creating rdf/base/src/Makefile
creating rdf/util/Makefile
creating rdf/util/public/Makefile
creating rdf/util/src/Makefile
creating rdf/build/Makefile
creating rdf/datasource/Makefile
creating rdf/datasource/public/Makefile
creating rdf/datasource/src/Makefile
creating rdf/tests/Makefile
creating rdf/tests/rdfcat/Makefile
creating rdf/tests/rdfpoll/Makefile
creating sun-java/Makefile
creating sun-java/stubs/Makefile
creating sun-java/stubs/include/Makefile
creating sun-java/stubs/jri/Makefile
creating themes/Makefile
creating themes/modern/Makefile
creating themes/classic/Makefile
creating uriloader/Makefile
creating uriloader/base/Makefile
creating view/Makefile
creating view/public/Makefile
creating view/src/Makefile
creating webshell/Makefile
creating webshell/public/Makefile
creating webshell/tests/Makefile
creating webshell/tests/viewer/Makefile
creating webshell/tests/viewer/public/Makefile
creating webshell/tests/viewer/unix/Makefile
creating webshell/tests/viewer/unix/gtk/Makefile
creating webshell/tests/viewer/unix/qt/Makefile
creating webshell/tests/viewer/unix/xlib/Makefile
creating widget/Makefile
creating widget/public/Makefile
creating widget/src/Makefile
creating widget/src/beos/Makefile
creating widget/src/build/Makefile
creating widget/src/gtk/Makefile
creating widget/src/gtksuperwin/Makefile
creating widget/src/gtkxtbin/Makefile
creating widget/src/qt/Makefile
creating widget/src/photon/Makefile
creating widget/src/mac/Makefile
creating widget/src/cocoa/Makefile
creating widget/src/xlib/Makefile
creating widget/src/os2/Makefile
creating widget/src/windows/Makefile
creating widget/src/xlibxtbin/Makefile
creating widget/src/xpwidgets/Makefile
creating widget/src/support/Makefile
creating xpcom/string/Makefile
creating xpcom/string/public/Makefile
creating xpcom/string/src/Makefile
creating xpcom/Makefile
creating xpcom/base/Makefile
creating xpcom/build/Makefile
creating xpcom/components/Makefile
creating xpcom/ds/Makefile
creating xpcom/glue/Makefile
creating xpcom/glue/standalone/Makefile
creating xpcom/io/Makefile
creating xpcom/typelib/Makefile
creating xpcom/reflect/Makefile
creating xpcom/typelib/xpt/Makefile
creating xpcom/typelib/xpt/public/Makefile
creating xpcom/typelib/xpt/src/Makefile
creating xpcom/typelib/xpt/tests/Makefile
creating xpcom/typelib/xpt/tools/Makefile
creating xpcom/typelib/xpidl/Makefile
creating xpcom/reflect/xptcall/Makefile
creating xpcom/reflect/xptcall/public/Makefile
creating xpcom/reflect/xptcall/src/Makefile
creating xpcom/reflect/xptcall/src/md/Makefile
creating xpcom/reflect/xptcall/src/md/os2/Makefile
creating xpcom/reflect/xptcall/src/md/test/Makefile
creating xpcom/reflect/xptcall/src/md/unix/Makefile
creating xpcom/reflect/xptcall/src/md/win32/Makefile
creating xpcom/reflect/xptcall/tests/Makefile
creating xpcom/reflect/xptinfo/Makefile
creating xpcom/reflect/xptinfo/public/Makefile
creating xpcom/reflect/xptinfo/src/Makefile
creating xpcom/reflect/xptinfo/tests/Makefile
creating xpcom/proxy/Makefile
creating xpcom/proxy/public/Makefile
creating xpcom/proxy/src/Makefile
creating xpcom/proxy/tests/Makefile
creating xpcom/sample/Makefile
creating xpcom/threads/Makefile
creating xpcom/tools/Makefile
creating xpcom/tools/registry/Makefile
creating xpcom/stub/Makefile
creating xpcom/windbgdlg/Makefile
creating xpcom/obsolete/Makefile
creating xpcom/obsolete/component/Makefile
creating xpcom/tests/Makefile
creating xpcom/tests/dynamic/Makefile
creating xpcom/tests/services/Makefile
creating xpcom/tests/windows/Makefile
creating js/src/xpconnect/Makefile
creating js/src/xpconnect/public/Makefile
creating js/src/xpconnect/idl/Makefile
creating js/src/xpconnect/shell/Makefile
creating js/src/xpconnect/src/Makefile
creating js/src/xpconnect/loader/Makefile
creating js/src/xpconnect/tests/Makefile
creating js/src/xpconnect/tests/components/Makefile
creating js/src/xpconnect/tests/idl/Makefile
creating js/src/xpconnect/tools/Makefile
creating js/src/xpconnect/tools/idl/Makefile
creating xpinstall/Makefile
creating xpinstall/packager/Makefile
creating xpinstall/packager/unix/Makefile
creating xpinstall/packager/windows/Makefile
creating xpinstall/packager/os2/Makefile
creating xpinstall/public/Makefile
creating xpinstall/res/Makefile
creating xpinstall/src/Makefile
creating xpinstall/stub/Makefile
creating xpinstall/wizard/libxpnet/Makefile
creating xpinstall/wizard/libxpnet/src/Makefile
creating xpinstall/wizard/libxpnet/test/Makefile
creating xpinstall/wizard/unix/src2/Makefile
creating xpinstall/wizard/windows/builder/Makefile
creating xpinstall/wizard/windows/nsinstall/Makefile
creating xpinstall/wizard/windows/nsztool/Makefile
creating xpinstall/wizard/windows/uninstall/Makefile
creating xpinstall/wizard/windows/setup/Makefile
creating xpinstall/wizard/windows/setuprsc/Makefile
creating xpinstall/wizard/windows/ren8dot3/Makefile
creating xpinstall/wizard/windows/ds32/Makefile
creating xpinstall/wizard/windows/GetShortPathName/Makefile
creating widget/src/xremoteclient/Makefile
creating toolkit/components/Makefile
creating toolkit/components/remote/Makefile
creating xpfe/Makefile
creating xpfe/browser/Makefile
creating xpfe/browser/public/Makefile
creating xpfe/browser/src/Makefile
creating xpfe/browser/samples/Makefile
creating xpfe/browser/samples/sampleimages/Makefile
creating xpfe/components/Makefile
creating xpfe/components/shistory/Makefile
creating xpfe/components/shistory/public/Makefile
creating xpfe/components/shistory/src/Makefile
creating xpfe/components/bookmarks/Makefile
creating xpfe/components/bookmarks/public/Makefile
creating xpfe/components/bookmarks/src/Makefile
creating xpfe/components/bookmarks/resources/Makefile
creating xpfe/components/directory/Makefile
creating xpfe/components/download-manager/Makefile
creating xpfe/components/download-manager/src/Makefile
creating xpfe/components/download-manager/public/Makefile
creating xpfe/components/download-manager/resources/Makefile
creating xpfe/components/extensions/Makefile
creating xpfe/components/extensions/src/Makefile
creating xpfe/components/extensions/public/Makefile
creating xpfe/components/find/Makefile
creating xpfe/components/find/public/Makefile
creating xpfe/components/find/src/Makefile
creating xpfe/components/filepicker/Makefile
creating xpfe/components/filepicker/public/Makefile
creating xpfe/components/filepicker/src/Makefile
creating xpfe/components/history/Makefile
creating xpfe/components/history/src/Makefile
creating xpfe/components/history/public/Makefile
creating xpfe/components/intl/Makefile
creating xpfe/components/prefwindow/Makefile
creating xpfe/components/prefwindow/resources/Makefile
creating xpfe/components/prefwindow/resources/content/Makefile
creating xpfe/components/prefwindow/resources/content/unix/Makefile
creating xpfe/components/prefwindow/resources/content/win/Makefile
creating xpfe/components/prefwindow/resources/locale/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/unix/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/win/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/mac/Makefile
creating xpfe/components/related/Makefile
creating xpfe/components/related/src/Makefile
creating xpfe/components/related/public/Makefile
creating xpfe/components/search/Makefile
creating xpfe/components/search/datasets/Makefile
creating xpfe/components/search/public/Makefile
creating xpfe/components/search/src/Makefile
creating xpfe/components/sidebar/Makefile
creating xpfe/components/sidebar/src/Makefile
creating xpfe/components/startup/Makefile
creating xpfe/components/startup/public/Makefile
creating xpfe/components/startup/src/Makefile
creating xpfe/components/autocomplete/Makefile
creating xpfe/components/autocomplete/public/Makefile
creating xpfe/components/autocomplete/src/Makefile
creating xpfe/components/updates/Makefile
creating xpfe/components/updates/src/Makefile
creating xpfe/components/urlwidget/Makefile
creating xpfe/components/winhooks/Makefile
creating xpfe/components/windowds/Makefile
creating xpfe/components/alerts/Makefile
creating xpfe/components/alerts/public/Makefile
creating xpfe/components/alerts/src/Makefile
creating xpfe/components/console/Makefile
creating xpfe/components/resetPref/Makefile
creating xpfe/components/killAll/Makefile
creating xpfe/components/build/Makefile
creating xpfe/components/xremote/Makefile
creating xpfe/components/xremote/public/Makefile
creating xpfe/components/xremote/src/Makefile
creating xpfe/appshell/Makefile
creating xpfe/appshell/src/Makefile
creating xpfe/appshell/public/Makefile
creating xpfe/bootstrap/Makefile
creating xpfe/bootstrap/init.d/Makefile
creating xpfe/bootstrap/appleevents/Makefile
creating xpfe/global/Makefile
creating xpfe/global/resources/Makefile
creating xpfe/global/resources/content/Makefile
creating xpfe/global/resources/content/os2/Makefile
creating xpfe/global/resources/content/unix/Makefile
creating xpfe/global/resources/locale/Makefile
creating xpfe/global/resources/locale/en-US/Makefile
creating xpfe/global/resources/locale/en-US/mac/Makefile
creating xpfe/global/resources/locale/en-US/os2/Makefile
creating xpfe/global/resources/locale/en-US/unix/Makefile
creating xpfe/global/resources/locale/en-US/win/Makefile
creating xpfe/communicator/Makefile
creating modules/zlib/Makefile
creating modules/zlib/src/Makefile
creating modules/zlib/standalone/Makefile
creating modules/libbz2/Makefile
creating modules/libbz2/src/Makefile
creating modules/libmar/Makefile
creating modules/libmar/src/Makefile
creating modules/libmar/tool/Makefile
creating security/manager/Makefile
creating security/manager/boot/Makefile
creating security/manager/boot/src/Makefile
creating security/manager/boot/public/Makefile
creating security/manager/ssl/Makefile
creating security/manager/ssl/src/Makefile
creating security/manager/ssl/resources/Makefile
creating security/manager/ssl/public/Makefile
creating security/manager/pki/Makefile
creating security/manager/pki/resources/Makefile
creating security/manager/pki/src/Makefile
creating security/manager/pki/public/Makefile
creating security/manager/locales/Makefile
creating calendar/Makefile
creating calendar/resources/Makefile
creating calendar/libical/Makefile
creating calendar/libical/src/Makefile
creating calendar/libical/src/libical/Makefile
creating calendar/libical/src/libicalss/Makefile
creating calendar/base/Makefile
creating calendar/base/public/Makefile
creating calendar/base/src/Makefile
creating calendar/base/build/Makefile
creating calendar/providers/Makefile
creating calendar/providers/memory/Makefile
creating calendar/providers/storage/Makefile
creating calendar/providers/composite/Makefile
creating calendar/timezones/Makefile
creating calendar/timezones/locales/Makefile
creating toolkit/Makefile
creating toolkit/library/Makefile
creating toolkit/content/Makefile
creating toolkit/obsolete/Makefile
creating toolkit/components/alerts/Makefile
creating toolkit/components/alerts/public/Makefile
creating toolkit/components/alerts/src/Makefile
creating toolkit/components/autocomplete/Makefile
creating toolkit/components/autocomplete/public/Makefile
creating toolkit/components/autocomplete/src/Makefile
creating toolkit/components/build/Makefile
creating toolkit/components/commandlines/Makefile
creating toolkit/components/commandlines/public/Makefile
creating toolkit/components/commandlines/src/Makefile
creating toolkit/components/console/Makefile
creating toolkit/components/cookie/Makefile
creating toolkit/components/downloads/public/Makefile
creating toolkit/components/downloads/Makefile
creating toolkit/components/downloads/src/Makefile
creating toolkit/components/filepicker/Makefile
creating toolkit/components/gnome/Makefile
creating toolkit/components/help/Makefile
creating toolkit/components/history/Makefile
creating toolkit/components/history/public/Makefile
creating toolkit/components/history/src/Makefile
creating toolkit/components/passwordmgr/Makefile
creating toolkit/components/passwordmgr/base/Makefile
creating toolkit/components/passwordmgr/resources/Makefile
creating toolkit/components/printing/Makefile
creating toolkit/components/satchel/Makefile
creating toolkit/components/satchel/public/Makefile
creating toolkit/components/satchel/src/Makefile
creating toolkit/components/startup/Makefile
creating toolkit/components/startup/public/Makefile
creating toolkit/components/startup/src/Makefile
creating toolkit/components/typeaheadfind/Makefile
creating toolkit/components/typeaheadfind/public/Makefile
creating toolkit/components/typeaheadfind/src/Makefile
creating toolkit/components/viewconfig/Makefile
creating toolkit/components/viewsource/Makefile
creating toolkit/locales/Makefile
creating toolkit/mozapps/Makefile
creating toolkit/mozapps/downloads/content/Makefile
creating toolkit/mozapps/downloads/Makefile
creating toolkit/mozapps/downloads/src/Makefile
creating toolkit/mozapps/extensions/Makefile
creating toolkit/mozapps/extensions/public/Makefile
creating toolkit/mozapps/extensions/src/Makefile
creating toolkit/mozapps/installer/unix/wizard/Makefile
creating toolkit/mozapps/installer/unix/Makefile
creating toolkit/mozapps/installer/Makefile
creating toolkit/mozapps/installer/windows/Makefile
creating toolkit/mozapps/installer/windows/wizard/Makefile
creating toolkit/mozapps/installer/windows/wizard/setup/Makefile
creating toolkit/mozapps/installer/windows/wizard/setuprsc/Makefile
creating toolkit/mozapps/installer/windows/wizard/uninstall/Makefile
creating toolkit/mozapps/update/Makefile
creating toolkit/mozapps/update/public/Makefile
creating toolkit/mozapps/update/src/Makefile
creating toolkit/mozapps/xpinstall/Makefile
creating toolkit/profile/Makefile
creating toolkit/profile/public/Makefile
creating toolkit/profile/skin/Makefile
creating toolkit/profile/src/Makefile
creating toolkit/themes/Makefile
creating toolkit/themes/gnomestripe/global/Makefile
creating toolkit/themes/gnomestripe/Makefile
creating toolkit/themes/pmstripe/global/Makefile
creating toolkit/themes/pmstripe/Makefile
creating toolkit/themes/pinstripe/communicator/Makefile
creating toolkit/themes/pinstripe/Makefile
creating toolkit/themes/pinstripe/global/Makefile
creating toolkit/themes/pinstripe/help/Makefile
creating toolkit/themes/pinstripe/mozapps/Makefile
creating toolkit/themes/winstripe/communicator/Makefile
creating toolkit/themes/winstripe/Makefile
creating toolkit/themes/winstripe/global/Makefile
creating toolkit/themes/winstripe/help/Makefile
creating toolkit/themes/winstripe/mozapps/Makefile
creating toolkit/xre/Makefile
creating calendar/installer/Makefile
creating calendar/installer/windows/Makefile
creating calendar/locales/Makefile
creating calendar/sunbird/Makefile
creating calendar/sunbird/app/Makefile
creating calendar/sunbird/base/Makefile
creating calendar/sunbird/locales/Makefile
creating db/sqlite3/src/Makefile
creating db/morkreader/Makefile
creating storage/Makefile
creating storage/public/Makefile
creating storage/src/Makefile
creating storage/build/Makefile
creating storage/test/Makefile
updating cache ./config.cache
creating ./config.status
creating config/autoconf.mk
creating config/doxygen.cfg
creating gfx/cairo/cairo/src/cairo-features.h
creating xpfe/global/buildconfig.html
creating toolkit/content/buildconfig.html
creating gfx/gfx-config.h
creating netwerk/necko-config.h
creating xpcom/xpcom-config.h
creating xpcom/xpcom-private.h
configuring in nsprpub
running /bin/sh ./configure  --enable-application=calendar --with-dist-prefix=/home/roger/mozilla/dist --with-mozilla --disable-debug --enable-optimize --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for whoami... (cached) /usr/bin/whoami
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... /usr/bin/ar
checking for ld... /usr/bin/ld
checking for strip... /usr/bin/strip
checking for windres... no
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking for perl5... (cached) /usr/bin/perl
checking for dlopen in -ldl... (cached) yes
checking for dlfcn.h... (cached) yes
checking whether gcc needs -traditional... (cached) no
checking for lchown... (cached) yes
checking for strerror... (cached) yes
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
updating cache .././config.cache
creating ./config.status
creating Makefile
creating config/Makefile
creating config/autoconf.mk
creating config/nsprincl.mk
creating config/nsprincl.sh
creating config/nspr-config
creating lib/Makefile
creating lib/ds/Makefile
creating lib/libc/Makefile
creating lib/libc/include/Makefile
creating lib/libc/src/Makefile
creating lib/tests/Makefile
creating pkg/Makefile
creating pkg/linux/Makefile
creating pkg/solaris/Makefile
creating pkg/solaris/SUNWpr/Makefile
creating pkg/solaris/SUNWprd/Makefile
creating pr/Makefile
creating pr/include/Makefile
creating pr/include/md/Makefile
creating pr/include/obsolete/Makefile
creating pr/include/private/Makefile
creating pr/src/Makefile
creating pr/src/io/Makefile
creating pr/src/linking/Makefile
creating pr/src/malloc/Makefile
creating pr/src/md/Makefile
creating pr/src/md/unix/Makefile
creating pr/src/memory/Makefile
creating pr/src/misc/Makefile
creating pr/src/threads/Makefile
creating pr/tests/Makefile
creating pr/tests/dll/Makefile
creating pr/src/pthreads/Makefile
configure: warning: Recreating autoconf.mk with updated nspr-config output
roger@roger-laptop:~/mozilla$ 

```

So, that seemed to run - hoped the last line wasn't important. Then ran make, and a staggering amount of readout finished in...

```
TestMinStringAPI.o: In function `test_adopt_sub()':
TestMinStringAPI.cpp:(.text+0x68a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
TestMinStringAPI.o: In function `test_adopt()':
TestMinStringAPI.cpp:(.text+0x73a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
/usr/bin/ld: TestMinStringAPI: hidden symbol `nsMemory::Clone(void const*, unsigned int)' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[3]: *** [TestMinStringAPI] Error 1
make[3]: Leaving directory `/home/roger/mozilla/xpcom/tests'
make[2]: *** [libs] Error 2
make[2]: Leaving directory `/home/roger/mozilla/xpcom'
make[1]: *** [tier_2] Error 2
make[1]: Leaving directory `/home/roger/mozilla'
make: *** [default] Error 2
roger@roger-laptop:~/mozilla$ 
```


You know, until this point I thought I had a chance of getting through this, but there's now so much info I can't digest or even post (due to sheer quantity). Does the above error mean anything to anyone? I'll post the enormous full output if it'll help

Thanks very much to both of you for your help, and I will understand if this is the end of the line!!

Cheers
Roger

---

### Post by rogerdean on 2008-09-26
ignore...

---

### Post by rogerdean on 2008-09-26
sorry, it's all above now

---

### Post by xeth_delta on 2008-09-26
> **rogerdean said:**
> Thanks xeth_delta

Right, good advice re the --help. That told me that the command I needed for Sunbird was ./configure --enable-application=calendar

```
roger@roger-laptop:~/mozilla$ ./configure --enable-application=calendar
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for nsinstall... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking for as... /usr/bin/as
checking for ar... ar
checking for ld... ld
checking for strip... strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for minimum required perl version >= 5.004... 5.008008
checking for full perl installation... yes
checking for doxygen... :
checking for whoami... /usr/bin/whoami
checking for autoconf... :
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for makedepend... /usr/bin/makedepend
checking for xargs... /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... no
checking whether ld has archive extraction flags... yes
checking that static assertion macros used in autoconf tests work... yes
checking for 64-bit OS... no
checking for ANSI C header files... yes
checking for working const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for st_blksize in struct stat... yes
checking for siginfo_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for int64... no
checking for uint... yes
checking for uint_t... no
checking for uint16_t... no
checking for uname.domainname... yes
checking for uname.__domainname... no
checking for usable wchar_t (2 bytes, unsigned)... no
checking for compiler -fshort-wchar option... yes
checking for visibility(hidden) attribute... yes
checking for visibility(default) attribute... yes
checking for visibility pragma support... yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for sys/byteorder.h... no
checking for compat.h... no
checking for getopt.h... yes
checking for sys/bitypes.h... yes
checking for memory.h... yes
checking for unistd.h... yes
checking for gnu/libc-version.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for X11/XKBlib.h... yes
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... no
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking for socket in -lsocket... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... no
checking for 8-bit clean memcmp... yes
checking for random... yes
checking for strerror... yes
checking for lchown... yes
checking for fchmod... yes
checking for snprintf... yes
checking for statvfs... yes
checking for memmove... yes
checking for rint... yes
checking for stat64... yes
checking for lstat64... yes
checking for flockfile... yes
checking for getpagesize... yes
checking for localtime_r... yes
checking for strtok_r... yes
checking for wcrtomb... yes
checking for mbrtowc... yes
checking for res_ninit()... yes
checking for gnu_get_libc_version()... yes
checking for iconv in -lc... yes
checking for iconv()... yes
checking for iconv() with const input... no
checking for nl_langinfo and CODESET... yes
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... yes
checking for C++ exceptions flag... -fno-exceptions
checking for gcc 3.0 ABI... yes
checking for C++ "explicit" keyword... yes
checking for C++ "typename" keyword... yes
checking for modern C++ template specialization syntax support... yes
checking whether partial template specialization works... yes
checking whether operators must be re-defined for templates derived from templates... no
checking whether we need to cast a derived template to pass as its base class... no
checking whether the compiler can resolve const ambiguities for templates... yes
checking whether the C++ "using" keyword can change access... yes
checking whether the C++ "using" keyword resolves ambiguity... yes
checking for "std::" namespace... yes
checking whether standard template operator!=() is ambiguous... unambiguous
checking for C++ reinterpret_cast... yes
checking for C++ dynamic_cast to void*... yes
checking whether C++ requires implementation of unused virtual methods... yes
checking for trouble comparing to zero near std::operator!=()... no
checking for LC_MESSAGES... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 1.3.7... yes
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for xft... yes
checking MOZ_XFT_CFLAGS... -I/usr/include/freetype2  
checking MOZ_XFT_LIBS...   -lXft -lfontconfig  
checking for pango >= 1.1.0... yes
checking _PANGOCHK_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS...   -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for XpGetPrinterList in -lXp... no
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... checking for gconf-2.0 >= 1.2.1... checking for libgnome-2.0 >= 2.0... checking for libgnomeui-2.0 >= 2.2.0... checking for valid optimization flags... yes
checking for __builtin_vec_new... no
checking for __builtin_vec_delete... no
checking for __builtin_new... no
checking for __builtin_delete... no
checking for __pure_virtual... no
checking for __cxa_demangle... yes
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking whether compiler supports -Wno-long-long... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0... yes
checking LIBIDL_CFLAGS... -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking LIBIDL_LIBS...   -lIDL-2 -lglib-2.0  
checking for glib-2.0 >= 1.3.7... yes
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS...   -lglib-2.0  
checking for stdint.h... yes
checking for inttypes.h... yes
checking for sys/int_types.h... no
creating mozilla-config.h
==== mozilla-config.h =================================
/* List of defines generated by configure. Included with preprocessor flag,
 * -include, to avoid long list of -D defines on the compile command-line.
 * Do not edit.
 */

#ifndef _MOZILLA_CONFIG_H_
#define _MOZILLA_CONFIG_H_

#define ACCESSIBILITY 1
#define D_INO d_ino
#define HAVE_DIRENT_H 1
#define HAVE_FCHMOD 1
#define HAVE_FLOCKFILE 1
#define HAVE_GETOPT_H 1
#define HAVE_GNU_GET_LIBC_VERSION 1
#define HAVE_GNU_LIBC_VERSION_H 1
#define HAVE_I18N_LC_MESSAGES 1
#define HAVE_INT16_T 1
#define HAVE_INT32_T 1
#define HAVE_INT64_T 1
#define HAVE_INTTYPES_H 1
#define HAVE_LANGINFO_CODESET 1
#define HAVE_LCHOWN 1
#define HAVE_LIBDL 1
#define HAVE_LIBM 1
#define HAVE_LOCALTIME_R 1
#define HAVE_LSTAT64 1
#define HAVE_MALLOC_H 1
#define HAVE_MEMMOVE 1
#define HAVE_MEMORY_H 1
#define HAVE_NL_TYPES_H 1
#define HAVE_RANDOM 1
#define HAVE_RES_NINIT 1
#define HAVE_RINT 1
#define HAVE_SIGINFO_T 1
#define HAVE_SNPRINTF 1
#define HAVE_STAT64 1
#define HAVE_STDINT_H 1
#define HAVE_STRERROR 1
#define HAVE_STRTOK_R 1
#define HAVE_ST_BLKSIZE 1
#define HAVE_SYS_BITYPES_H 1
#define HAVE_SYS_CDEFS_H 1
#define HAVE_SYS_STATFS_H 1
#define HAVE_SYS_STATVFS_H 1
#define HAVE_UINT 1
#define HAVE_UINT64_T 1
#define HAVE_UNAME_DOMAINNAME_FIELD 1
#define HAVE_UNISTD_H 1
#define HAVE_VA_COPY 1
#define HAVE_VISIBILITY_ATTRIBUTE 1
#define HAVE_VISIBILITY_HIDDEN_ATTRIBUTE 1
#define HAVE_X11_XKBLIB_H 1
#define HAVE___CXA_DEMANGLE 1
#define IBMBIDI 1
#define JS_THREADSAFE 1
#define MOZILLA_1_8_BRANCH 1
#define MOZILLA_LOCALE_VERSION "1.8.1"
#define MOZILLA_REGION_VERSION "1.8.1"
#define MOZILLA_SKIN_VERSION "1.8"
#define MOZILLA_VERSION "1.8.1.18pre"
#define MOZILLA_VERSION_U 1.8.1.18pre
#define MOZ_ACCESSIBILITY_ATK 1
#define MOZ_BUILD_APP calendar
#define MOZ_DEFAULT_TOOLKIT "gtk2"
#define MOZ_DISTRIBUTION_ID "org.mozilla"
#define MOZ_DLL_SUFFIX ".so"
#define MOZ_ENABLE_CANVAS 1
#define MOZ_ENABLE_OLD_ABI_COMPAT_WRAPPERS 1
#define MOZ_ENABLE_XFT 1
#define MOZ_ENABLE_XREMOTE 1
#define MOZ_FEEDS 1
#define MOZ_JSLOADER 1
#define MOZ_LOGGING 1
#define MOZ_MORK 1
#define MOZ_PROFILELOCKING 1
#define MOZ_STORAGE 1
#define MOZ_SUNBIRD 1
#define MOZ_UPDATE_CHANNEL default
#define MOZ_USER_DIR ".mozilla"
#define MOZ_VIEW_SOURCE 1
#define MOZ_WIDGET_GTK2 1
#define MOZ_X11 1
#define MOZ_XPINSTALL 1
#define MOZ_XTF 1
#define MOZ_XUL 1
#define MOZ_XUL_APP 1
#define NO_X11 1
#define NS_PRINTING 1
#define NS_PRINT_PREVIEW 1
#define STDC_HEADERS 1
#define UNIX_ASYNC_DNS 1
#define VA_COPY va_copy
#define XP_UNIX 1
#define X_DISPLAY_MISSING 1
#define _REENTRANT 1

#endif /* _MOZILLA_CONFIG_H_ */

creating Makefile
creating build/Makefile
creating build/unix/Makefile
creating config/Makefile
creating config/mkdepend/Makefile
creating caps/Makefile
creating caps/idl/Makefile
creating caps/include/Makefile
creating caps/src/Makefile
creating chrome/Makefile
creating chrome/public/Makefile
creating chrome/src/Makefile
creating embedding/minimo/chromelite/Makefile
creating rdf/chrome/Makefile
creating rdf/chrome/public/Makefile
creating rdf/chrome/build/Makefile
creating rdf/chrome/src/Makefile
creating rdf/chrome/tools/Makefile
creating rdf/chrome/tools/chromereg/Makefile
creating db/Makefile
creating db/mdb/Makefile
creating db/mdb/public/Makefile
creating db/mork/Makefile
creating db/mork/build/Makefile
creating db/mork/src/Makefile
creating dbm/Makefile
creating dbm/include/Makefile
creating dbm/src/Makefile
creating dbm/tests/Makefile
creating docshell/Makefile
creating docshell/base/Makefile
creating docshell/build/Makefile
creating dom/Makefile
creating dom/public/Makefile
creating dom/public/base/Makefile
creating dom/public/coreEvents/Makefile
creating dom/public/idl/Makefile
creating dom/public/idl/base/Makefile
creating dom/public/idl/canvas/Makefile
creating dom/public/idl/core/Makefile
creating dom/public/idl/css/Makefile
creating dom/public/idl/events/Makefile
creating dom/public/idl/html/Makefile
creating dom/public/idl/range/Makefile
creating dom/public/idl/stylesheets/Makefile
creating dom/public/idl/views/Makefile
creating dom/public/idl/xbl/Makefile
creating dom/public/idl/xpath/Makefile
creating dom/public/idl/xul/Makefile
creating dom/src/Makefile
creating dom/src/base/Makefile
creating dom/src/events/Makefile
creating dom/src/jsurl/Makefile
creating dom/locales/Makefile
creating editor/Makefile
creating editor/public/Makefile
creating editor/idl/Makefile
creating editor/txmgr/Makefile
creating editor/txmgr/idl/Makefile
creating editor/txmgr/public/Makefile
creating editor/txmgr/src/Makefile
creating editor/txmgr/tests/Makefile
creating editor/txtsvc/Makefile
creating editor/txtsvc/public/Makefile
creating editor/txtsvc/src/Makefile
creating embedding/Makefile
creating embedding/base/Makefile
creating embedding/browser/Makefile
creating embedding/browser/activex/src/Makefile
creating embedding/browser/activex/src/control/Makefile
creating embedding/browser/activex/src/control_kicker/Makefile
creating embedding/browser/build/Makefile
creating embedding/browser/chrome/Makefile
creating embedding/browser/webBrowser/Makefile
creating embedding/browser/gtk/Makefile
creating embedding/browser/gtk/src/Makefile
creating embedding/browser/gtk/tests/Makefile
creating embedding/browser/qt/Makefile
creating embedding/browser/qt/src/Makefile
creating embedding/browser/qt/tests/Makefile
creating embedding/browser/photon/Makefile
creating embedding/browser/photon/src/Makefile
creating embedding/browser/photon/tests/Makefile
creating embedding/browser/cocoa/Makefile
creating embedding/components/Makefile
creating embedding/components/build/Makefile
creating embedding/components/windowwatcher/Makefile
creating embedding/components/windowwatcher/public/Makefile
creating embedding/components/windowwatcher/src/Makefile
creating embedding/components/ui/Makefile
creating embedding/components/ui/helperAppDlg/Makefile
creating embedding/components/ui/progressDlg/Makefile
creating embedding/config/Makefile
creating embedding/tests/Makefile
creating embedding/tests/cocoaEmbed/Makefile
creating embedding/tests/winEmbed/Makefile
creating embedding/tests/mfcembed/Makefile
creating embedding/tests/mfcembed/components/Makefile
creating parser/expat/Makefile
creating parser/expat/lib/Makefile
creating extensions/Makefile
creating extensions/xmlextras/Makefile
creating extensions/xmlextras/pointers/Makefile
creating extensions/xmlextras/pointers/src/Makefile
creating extensions/xmlextras/build/Makefile
creating extensions/xmlextras/build/src/Makefile
creating extensions/transformiix/source/base/Makefile
creating extensions/transformiix/source/main/Makefile
creating extensions/transformiix/source/xml/dom/standalone/Makefile
creating extensions/transformiix/source/xml/dom/Makefile
creating extensions/transformiix/source/xml/parser/Makefile
creating extensions/transformiix/source/xml/Makefile
creating extensions/transformiix/source/xpath/Makefile
creating extensions/transformiix/source/xslt/functions/Makefile
creating extensions/transformiix/source/xslt/util/Makefile
creating extensions/transformiix/source/xslt/Makefile
creating extensions/transformiix/source/Makefile
creating extensions/transformiix/Makefile
creating extensions/transformiix/resources/Makefile
creating gc/boehm/Makefile
creating gc/boehm/leaksoup/Makefile
creating gfx/Makefile
creating gfx/idl/Makefile
creating gfx/public/Makefile
creating gfx/src/Makefile
creating gfx/src/beos/Makefile
creating gfx/src/gtk/Makefile
creating gfx/src/ps/Makefile
creating gfx/src/psshared/Makefile
creating gfx/src/photon/Makefile
creating gfx/src/mac/Makefile
creating gfx/src/qt/Makefile
creating gfx/src/xlib/Makefile
creating gfx/src/os2/Makefile
creating gfx/src/xlibrgb/Makefile
creating gfx/src/windows/Makefile
creating gfx/src/cairo/Makefile
creating gfx/tests/Makefile
creating gfx/cairo/Makefile
creating gfx/cairo/libpixman/src/Makefile
creating gfx/cairo/cairo/src/Makefile
creating accessible/Makefile
creating accessible/public/Makefile
creating accessible/public/msaa/Makefile
creating accessible/src/Makefile
creating accessible/src/base/Makefile
creating accessible/src/html/Makefile
creating accessible/src/xul/Makefile
creating accessible/src/msaa/Makefile
creating accessible/src/atk/Makefile
creating accessible/src/mac/Makefile
creating accessible/build/Makefile
creating parser/htmlparser/Makefile
creating parser/htmlparser/robot/Makefile
creating parser/htmlparser/robot/test/Makefile
creating parser/htmlparser/public/Makefile
creating parser/htmlparser/src/Makefile
creating parser/htmlparser/tests/Makefile
creating parser/htmlparser/tests/grabpage/Makefile
creating parser/htmlparser/tests/logparse/Makefile
creating parser/htmlparser/tests/html/Makefile
creating parser/htmlparser/tests/outsinks/Makefile
creating intl/Makefile
creating intl/chardet/Makefile
creating intl/chardet/public/Makefile
creating intl/chardet/src/Makefile
creating intl/uconv/Makefile
creating intl/uconv/idl/Makefile
creating intl/uconv/public/Makefile
creating intl/uconv/src/Makefile
creating intl/uconv/tests/Makefile
creating intl/uconv/ucvja/Makefile
creating intl/uconv/ucvlatin/Makefile
creating intl/uconv/ucvcn/Makefile
creating intl/uconv/ucvtw/Makefile
creating intl/uconv/ucvtw2/Makefile
creating intl/uconv/ucvko/Makefile
creating intl/uconv/ucvibm/Makefile
creating intl/uconv/native/Makefile
creating intl/locale/Makefile
creating intl/locale/public/Makefile
creating intl/locale/idl/Makefile
creating intl/locale/src/Makefile
creating intl/locale/src/unix/Makefile
creating intl/locale/src/os2/Makefile
creating intl/locale/src/windows/Makefile
creating intl/locale/tests/Makefile
creating intl/lwbrk/Makefile
creating intl/lwbrk/src/Makefile
creating intl/lwbrk/public/Makefile
creating intl/lwbrk/tests/Makefile
creating intl/unicharutil/Makefile
creating intl/unicharutil/idl/Makefile
creating intl/unicharutil/src/Makefile
creating intl/unicharutil/public/Makefile
creating intl/unicharutil/tables/Makefile
creating intl/unicharutil/tests/Makefile
creating intl/unicharutil/tools/Makefile
creating intl/strres/Makefile
creating intl/strres/public/Makefile
creating intl/strres/src/Makefile
creating intl/strres/tests/Makefile
creating jpeg/Makefile
creating js/Makefile
creating js/src/Makefile
creating js/src/fdlibm/Makefile
creating js/jsd/Makefile
creating js/jsd/idl/Makefile
creating content/Makefile
creating content/base/Makefile
creating content/base/public/Makefile
creating content/base/src/Makefile
creating content/canvas/Makefile
creating content/canvas/public/Makefile
creating content/canvas/src/Makefile
creating content/events/Makefile
creating content/events/public/Makefile
creating content/events/src/Makefile
creating content/html/Makefile
creating content/html/content/Makefile
creating content/html/content/public/Makefile
creating content/html/content/src/Makefile
creating content/html/document/Makefile
creating content/html/document/public/Makefile
creating content/html/document/src/Makefile
creating content/xml/Makefile
creating content/xml/content/Makefile
creating content/xml/content/public/Makefile
creating content/xml/content/src/Makefile
creating content/xml/document/Makefile
creating content/xml/document/public/Makefile
creating content/xml/document/src/Makefile
creating content/xul/Makefile
creating content/xul/content/Makefile
creating content/xul/content/public/Makefile
creating content/xul/content/src/Makefile
creating content/xul/document/Makefile
creating content/xul/document/public/Makefile
creating content/xul/document/src/Makefile
creating content/xul/templates/public/Makefile
creating content/xul/templates/src/Makefile
creating content/xbl/Makefile
creating content/xbl/public/Makefile
creating content/xbl/src/Makefile
creating content/xbl/builtin/Makefile
creating content/xsl/Makefile
creating content/xsl/public/Makefile
creating content/xtf/Makefile
creating content/xtf/public/Makefile
creating content/xtf/src/Makefile
creating layout/Makefile
creating layout/base/Makefile
creating layout/base/tests/Makefile
creating layout/build/Makefile
creating layout/forms/Makefile
creating layout/html/tests/Makefile
creating layout/style/Makefile
creating layout/printing/Makefile
creating layout/tools/Makefile
creating layout/xul/Makefile
creating layout/xul/base/Makefile
creating layout/xul/base/public/Makefile
creating layout/xul/base/src/Makefile
creating layout/xul/base/src/tree/Makefile
creating layout/xul/base/src/tree/src/Makefile
creating layout/xul/base/src/tree/public/Makefile
creating layout/xtf/Makefile
creating layout/xtf/src/Makefile
creating modules/libreg/Makefile
creating modules/libreg/include/Makefile
creating modules/libreg/src/Makefile
creating modules/libreg/standalone/Makefile
creating modules/libimg/Makefile
creating modules/libimg/png/Makefile
creating modules/libpr0n/Makefile
creating modules/libpr0n/public/Makefile
creating modules/libpr0n/src/Makefile
creating modules/libpr0n/decoders/Makefile
creating modules/libpr0n/decoders/gif/Makefile
creating modules/libpr0n/decoders/png/Makefile
creating modules/libpr0n/decoders/jpeg/Makefile
creating modules/libpr0n/decoders/bmp/Makefile
creating modules/libpr0n/decoders/icon/Makefile
creating modules/libpr0n/decoders/icon/win/Makefile
creating modules/libpr0n/decoders/icon/gtk/Makefile
creating modules/libpr0n/decoders/icon/beos/Makefile
creating modules/libpr0n/decoders/xbm/Makefile
creating modules/libjar/Makefile
creating modules/libjar/standalone/Makefile
creating modules/libpref/Makefile
creating modules/libpref/public/Makefile
creating modules/libpref/src/Makefile
creating modules/libutil/Makefile
creating modules/libutil/public/Makefile
creating modules/libutil/src/Makefile
creating js/src/liveconnect/Makefile
creating js/src/liveconnect/classes/Makefile
creating modules/oji/Makefile
creating modules/oji/public/Makefile
creating modules/oji/src/Makefile
creating plugin/oji/JEP/Makefile
creating modules/plugin/Makefile
creating modules/plugin/base/src/Makefile
creating modules/plugin/base/public/Makefile
creating modules/plugin/samples/simple/Makefile
creating modules/plugin/samples/SanePlugin/Makefile
creating modules/plugin/samples/default/unix/Makefile
creating modules/plugin/tools/sdk/Makefile
creating modules/plugin/tools/sdk/samples/Makefile
creating modules/plugin/tools/sdk/samples/common/Makefile
creating modules/plugin/tools/sdk/samples/basic/windows/Makefile
creating modules/plugin/tools/sdk/samples/scriptable/windows/Makefile
creating modules/plugin/tools/sdk/samples/simple/Makefile
creating modules/plugin/tools/sdk/samples/winless/windows/Makefile
creating netwerk/Makefile
creating netwerk/base/Makefile
creating netwerk/base/public/Makefile
creating netwerk/base/src/Makefile
creating netwerk/build/Makefile
creating netwerk/build2/Makefile
creating netwerk/cache/Makefile
creating netwerk/cache/public/Makefile
creating netwerk/cache/src/Makefile
creating netwerk/cookie/Makefile
creating netwerk/cookie/public/Makefile
creating netwerk/cookie/src/Makefile
creating netwerk/dns/Makefile
creating netwerk/dns/public/Makefile
creating netwerk/dns/src/Makefile
creating netwerk/protocol/Makefile
creating netwerk/protocol/about/Makefile
creating netwerk/protocol/about/public/Makefile
creating netwerk/protocol/about/src/Makefile
creating netwerk/protocol/data/Makefile
creating netwerk/protocol/data/public/Makefile
creating netwerk/protocol/data/src/Makefile
creating netwerk/protocol/file/Makefile
creating netwerk/protocol/file/public/Makefile
creating netwerk/protocol/file/src/Makefile
creating netwerk/protocol/ftp/Makefile
creating netwerk/protocol/ftp/public/Makefile
creating netwerk/protocol/ftp/src/Makefile
creating netwerk/protocol/gopher/Makefile
creating netwerk/protocol/gopher/src/Makefile
creating netwerk/protocol/http/Makefile
creating netwerk/protocol/http/public/Makefile
creating netwerk/protocol/http/src/Makefile
creating netwerk/protocol/res/Makefile
creating netwerk/protocol/res/public/Makefile
creating netwerk/protocol/res/src/Makefile
creating netwerk/mime/Makefile
creating netwerk/mime/public/Makefile
creating netwerk/mime/src/Makefile
creating netwerk/socket/Makefile
creating netwerk/socket/base/Makefile
creating netwerk/streamconv/Makefile
creating netwerk/streamconv/converters/Makefile
creating netwerk/streamconv/public/Makefile
creating netwerk/streamconv/src/Makefile
creating netwerk/streamconv/test/Makefile
creating netwerk/test/Makefile
creating netwerk/testserver/Makefile
creating netwerk/resources/Makefile
creating netwerk/locales/Makefile
creating netwerk/system/Makefile
creating netwerk/system/win32/Makefile
creating uriloader/exthandler/Makefile
creating profile/Makefile
creating profile/src/Makefile
creating profile/public/Makefile
creating profile/resources/Makefile
creating profile/pref-migrator/Makefile
creating profile/pref-migrator/public/Makefile
creating profile/pref-migrator/src/Makefile
creating profile/pref-migrator/resources/Makefile
creating profile/defaults/Makefile
creating profile/dirserviceprovider/Makefile
creating profile/dirserviceprovider/public/Makefile
creating profile/dirserviceprovider/src/Makefile
creating rdf/Makefile
creating rdf/base/Makefile
creating rdf/base/idl/Makefile
creating rdf/base/public/Makefile
creating rdf/base/src/Makefile
creating rdf/util/Makefile
creating rdf/util/public/Makefile
creating rdf/util/src/Makefile
creating rdf/build/Makefile
creating rdf/datasource/Makefile
creating rdf/datasource/public/Makefile
creating rdf/datasource/src/Makefile
creating rdf/tests/Makefile
creating rdf/tests/rdfcat/Makefile
creating rdf/tests/rdfpoll/Makefile
creating sun-java/Makefile
creating sun-java/stubs/Makefile
creating sun-java/stubs/include/Makefile
creating sun-java/stubs/jri/Makefile
creating themes/Makefile
creating themes/modern/Makefile
creating themes/classic/Makefile
creating uriloader/Makefile
creating uriloader/base/Makefile
creating view/Makefile
creating view/public/Makefile
creating view/src/Makefile
creating webshell/Makefile
creating webshell/public/Makefile
creating webshell/tests/Makefile
creating webshell/tests/viewer/Makefile
creating webshell/tests/viewer/public/Makefile
creating webshell/tests/viewer/unix/Makefile
creating webshell/tests/viewer/unix/gtk/Makefile
creating webshell/tests/viewer/unix/qt/Makefile
creating webshell/tests/viewer/unix/xlib/Makefile
creating widget/Makefile
creating widget/public/Makefile
creating widget/src/Makefile
creating widget/src/beos/Makefile
creating widget/src/build/Makefile
creating widget/src/gtk/Makefile
creating widget/src/gtksuperwin/Makefile
creating widget/src/gtkxtbin/Makefile
creating widget/src/qt/Makefile
creating widget/src/photon/Makefile
creating widget/src/mac/Makefile
creating widget/src/cocoa/Makefile
creating widget/src/xlib/Makefile
creating widget/src/os2/Makefile
creating widget/src/windows/Makefile
creating widget/src/xlibxtbin/Makefile
creating widget/src/xpwidgets/Makefile
creating widget/src/support/Makefile
creating xpcom/string/Makefile
creating xpcom/string/public/Makefile
creating xpcom/string/src/Makefile
creating xpcom/Makefile
creating xpcom/base/Makefile
creating xpcom/build/Makefile
creating xpcom/components/Makefile
creating xpcom/ds/Makefile
creating xpcom/glue/Makefile
creating xpcom/glue/standalone/Makefile
creating xpcom/io/Makefile
creating xpcom/typelib/Makefile
creating xpcom/reflect/Makefile
creating xpcom/typelib/xpt/Makefile
creating xpcom/typelib/xpt/public/Makefile
creating xpcom/typelib/xpt/src/Makefile
creating xpcom/typelib/xpt/tests/Makefile
creating xpcom/typelib/xpt/tools/Makefile
creating xpcom/typelib/xpidl/Makefile
creating xpcom/reflect/xptcall/Makefile
creating xpcom/reflect/xptcall/public/Makefile
creating xpcom/reflect/xptcall/src/Makefile
creating xpcom/reflect/xptcall/src/md/Makefile
creating xpcom/reflect/xptcall/src/md/os2/Makefile
creating xpcom/reflect/xptcall/src/md/test/Makefile
creating xpcom/reflect/xptcall/src/md/unix/Makefile
creating xpcom/reflect/xptcall/src/md/win32/Makefile
creating xpcom/reflect/xptcall/tests/Makefile
creating xpcom/reflect/xptinfo/Makefile
creating xpcom/reflect/xptinfo/public/Makefile
creating xpcom/reflect/xptinfo/src/Makefile
creating xpcom/reflect/xptinfo/tests/Makefile
creating xpcom/proxy/Makefile
creating xpcom/proxy/public/Makefile
creating xpcom/proxy/src/Makefile
creating xpcom/proxy/tests/Makefile
creating xpcom/sample/Makefile
creating xpcom/threads/Makefile
creating xpcom/tools/Makefile
creating xpcom/tools/registry/Makefile
creating xpcom/stub/Makefile
creating xpcom/windbgdlg/Makefile
creating xpcom/obsolete/Makefile
creating xpcom/obsolete/component/Makefile
creating xpcom/tests/Makefile
creating xpcom/tests/dynamic/Makefile
creating xpcom/tests/services/Makefile
creating xpcom/tests/windows/Makefile
creating js/src/xpconnect/Makefile
creating js/src/xpconnect/public/Makefile
creating js/src/xpconnect/idl/Makefile
creating js/src/xpconnect/shell/Makefile
creating js/src/xpconnect/src/Makefile
creating js/src/xpconnect/loader/Makefile
creating js/src/xpconnect/tests/Makefile
creating js/src/xpconnect/tests/components/Makefile
creating js/src/xpconnect/tests/idl/Makefile
creating js/src/xpconnect/tools/Makefile
creating js/src/xpconnect/tools/idl/Makefile
creating xpinstall/Makefile
creating xpinstall/packager/Makefile
creating xpinstall/packager/unix/Makefile
creating xpinstall/packager/windows/Makefile
creating xpinstall/packager/os2/Makefile
creating xpinstall/public/Makefile
creating xpinstall/res/Makefile
creating xpinstall/src/Makefile
creating xpinstall/stub/Makefile
creating xpinstall/wizard/libxpnet/Makefile
creating xpinstall/wizard/libxpnet/src/Makefile
creating xpinstall/wizard/libxpnet/test/Makefile
creating xpinstall/wizard/unix/src2/Makefile
creating xpinstall/wizard/windows/builder/Makefile
creating xpinstall/wizard/windows/nsinstall/Makefile
creating xpinstall/wizard/windows/nsztool/Makefile
creating xpinstall/wizard/windows/uninstall/Makefile
creating xpinstall/wizard/windows/setup/Makefile
creating xpinstall/wizard/windows/setuprsc/Makefile
creating xpinstall/wizard/windows/ren8dot3/Makefile
creating xpinstall/wizard/windows/ds32/Makefile
creating xpinstall/wizard/windows/GetShortPathName/Makefile
creating widget/src/xremoteclient/Makefile
creating toolkit/components/Makefile
creating toolkit/components/remote/Makefile
creating xpfe/Makefile
creating xpfe/browser/Makefile
creating xpfe/browser/public/Makefile
creating xpfe/browser/src/Makefile
creating xpfe/browser/samples/Makefile
creating xpfe/browser/samples/sampleimages/Makefile
creating xpfe/components/Makefile
creating xpfe/components/shistory/Makefile
creating xpfe/components/shistory/public/Makefile
creating xpfe/components/shistory/src/Makefile
creating xpfe/components/bookmarks/Makefile
creating xpfe/components/bookmarks/public/Makefile
creating xpfe/components/bookmarks/src/Makefile
creating xpfe/components/bookmarks/resources/Makefile
creating xpfe/components/directory/Makefile
creating xpfe/components/download-manager/Makefile
creating xpfe/components/download-manager/src/Makefile
creating xpfe/components/download-manager/public/Makefile
creating xpfe/components/download-manager/resources/Makefile
creating xpfe/components/extensions/Makefile
creating xpfe/components/extensions/src/Makefile
creating xpfe/components/extensions/public/Makefile
creating xpfe/components/find/Makefile
creating xpfe/components/find/public/Makefile
creating xpfe/components/find/src/Makefile
creating xpfe/components/filepicker/Makefile
creating xpfe/components/filepicker/public/Makefile
creating xpfe/components/filepicker/src/Makefile
creating xpfe/components/history/Makefile
creating xpfe/components/history/src/Makefile
creating xpfe/components/history/public/Makefile
creating xpfe/components/intl/Makefile
creating xpfe/components/prefwindow/Makefile
creating xpfe/components/prefwindow/resources/Makefile
creating xpfe/components/prefwindow/resources/content/Makefile
creating xpfe/components/prefwindow/resources/content/unix/Makefile
creating xpfe/components/prefwindow/resources/content/win/Makefile
creating xpfe/components/prefwindow/resources/locale/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/unix/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/win/Makefile
creating xpfe/components/prefwindow/resources/locale/en-US/mac/Makefile
creating xpfe/components/related/Makefile
creating xpfe/components/related/src/Makefile
creating xpfe/components/related/public/Makefile
creating xpfe/components/search/Makefile
creating xpfe/components/search/datasets/Makefile
creating xpfe/components/search/public/Makefile
creating xpfe/components/search/src/Makefile
creating xpfe/components/sidebar/Makefile
creating xpfe/components/sidebar/src/Makefile
creating xpfe/components/startup/Makefile
creating xpfe/components/startup/public/Makefile
creating xpfe/components/startup/src/Makefile
creating xpfe/components/autocomplete/Makefile
creating xpfe/components/autocomplete/public/Makefile
creating xpfe/components/autocomplete/src/Makefile
creating xpfe/components/updates/Makefile
creating xpfe/components/updates/src/Makefile
creating xpfe/components/urlwidget/Makefile
creating xpfe/components/winhooks/Makefile
creating xpfe/components/windowds/Makefile
creating xpfe/components/alerts/Makefile
creating xpfe/components/alerts/public/Makefile
creating xpfe/components/alerts/src/Makefile
creating xpfe/components/console/Makefile
creating xpfe/components/resetPref/Makefile
creating xpfe/components/killAll/Makefile
creating xpfe/components/build/Makefile
creating xpfe/components/xremote/Makefile
creating xpfe/components/xremote/public/Makefile
creating xpfe/components/xremote/src/Makefile
creating xpfe/appshell/Makefile
creating xpfe/appshell/src/Makefile
creating xpfe/appshell/public/Makefile
creating xpfe/bootstrap/Makefile
creating xpfe/bootstrap/init.d/Makefile
creating xpfe/bootstrap/appleevents/Makefile
creating xpfe/global/Makefile
creating xpfe/global/resources/Makefile
creating xpfe/global/resources/content/Makefile
creating xpfe/global/resources/content/os2/Makefile
creating xpfe/global/resources/content/unix/Makefile
creating xpfe/global/resources/locale/Makefile
creating xpfe/global/resources/locale/en-US/Makefile
creating xpfe/global/resources/locale/en-US/mac/Makefile
creating xpfe/global/resources/locale/en-US/os2/Makefile
creating xpfe/global/resources/locale/en-US/unix/Makefile
creating xpfe/global/resources/locale/en-US/win/Makefile
creating xpfe/communicator/Makefile
creating modules/zlib/Makefile
creating modules/zlib/src/Makefile
creating modules/zlib/standalone/Makefile
creating modules/libbz2/Makefile
creating modules/libbz2/src/Makefile
creating modules/libmar/Makefile
creating modules/libmar/src/Makefile
creating modules/libmar/tool/Makefile
creating security/manager/Makefile
creating security/manager/boot/Makefile
creating security/manager/boot/src/Makefile
creating security/manager/boot/public/Makefile
creating security/manager/ssl/Makefile
creating security/manager/ssl/src/Makefile
creating security/manager/ssl/resources/Makefile
creating security/manager/ssl/public/Makefile
creating security/manager/pki/Makefile
creating security/manager/pki/resources/Makefile
creating security/manager/pki/src/Makefile
creating security/manager/pki/public/Makefile
creating security/manager/locales/Makefile
creating calendar/Makefile
creating calendar/resources/Makefile
creating calendar/libical/Makefile
creating calendar/libical/src/Makefile
creating calendar/libical/src/libical/Makefile
creating calendar/libical/src/libicalss/Makefile
creating calendar/base/Makefile
creating calendar/base/public/Makefile
creating calendar/base/src/Makefile
creating calendar/base/build/Makefile
creating calendar/providers/Makefile
creating calendar/providers/memory/Makefile
creating calendar/providers/storage/Makefile
creating calendar/providers/composite/Makefile
creating calendar/timezones/Makefile
creating calendar/timezones/locales/Makefile
creating toolkit/Makefile
creating toolkit/library/Makefile
creating toolkit/content/Makefile
creating toolkit/obsolete/Makefile
creating toolkit/components/alerts/Makefile
creating toolkit/components/alerts/public/Makefile
creating toolkit/components/alerts/src/Makefile
creating toolkit/components/autocomplete/Makefile
creating toolkit/components/autocomplete/public/Makefile
creating toolkit/components/autocomplete/src/Makefile
creating toolkit/components/build/Makefile
creating toolkit/components/commandlines/Makefile
creating toolkit/components/commandlines/public/Makefile
creating toolkit/components/commandlines/src/Makefile
creating toolkit/components/console/Makefile
creating toolkit/components/cookie/Makefile
creating toolkit/components/downloads/public/Makefile
creating toolkit/components/downloads/Makefile
creating toolkit/components/downloads/src/Makefile
creating toolkit/components/filepicker/Makefile
creating toolkit/components/gnome/Makefile
creating toolkit/components/help/Makefile
creating toolkit/components/history/Makefile
creating toolkit/components/history/public/Makefile
creating toolkit/components/history/src/Makefile
creating toolkit/components/passwordmgr/Makefile
creating toolkit/components/passwordmgr/base/Makefile
creating toolkit/components/passwordmgr/resources/Makefile
creating toolkit/components/printing/Makefile
creating toolkit/components/satchel/Makefile
creating toolkit/components/satchel/public/Makefile
creating toolkit/components/satchel/src/Makefile
creating toolkit/components/startup/Makefile
creating toolkit/components/startup/public/Makefile
creating toolkit/components/startup/src/Makefile
creating toolkit/components/typeaheadfind/Makefile
creating toolkit/components/typeaheadfind/public/Makefile
creating toolkit/components/typeaheadfind/src/Makefile
creating toolkit/components/viewconfig/Makefile
creating toolkit/components/viewsource/Makefile
creating toolkit/locales/Makefile
creating toolkit/mozapps/Makefile
creating toolkit/mozapps/downloads/content/Makefile
creating toolkit/mozapps/downloads/Makefile
creating toolkit/mozapps/downloads/src/Makefile
creating toolkit/mozapps/extensions/Makefile
creating toolkit/mozapps/extensions/public/Makefile
creating toolkit/mozapps/extensions/src/Makefile
creating toolkit/mozapps/installer/unix/wizard/Makefile
creating toolkit/mozapps/installer/unix/Makefile
creating toolkit/mozapps/installer/Makefile
creating toolkit/mozapps/installer/windows/Makefile
creating toolkit/mozapps/installer/windows/wizard/Makefile
creating toolkit/mozapps/installer/windows/wizard/setup/Makefile
creating toolkit/mozapps/installer/windows/wizard/setuprsc/Makefile
creating toolkit/mozapps/installer/windows/wizard/uninstall/Makefile
creating toolkit/mozapps/update/Makefile
creating toolkit/mozapps/update/public/Makefile
creating toolkit/mozapps/update/src/Makefile
creating toolkit/mozapps/xpinstall/Makefile
creating toolkit/profile/Makefile
creating toolkit/profile/public/Makefile
creating toolkit/profile/skin/Makefile
creating toolkit/profile/src/Makefile
creating toolkit/themes/Makefile
creating toolkit/themes/gnomestripe/global/Makefile
creating toolkit/themes/gnomestripe/Makefile
creating toolkit/themes/pmstripe/global/Makefile
creating toolkit/themes/pmstripe/Makefile
creating toolkit/themes/pinstripe/communicator/Makefile
creating toolkit/themes/pinstripe/Makefile
creating toolkit/themes/pinstripe/global/Makefile
creating toolkit/themes/pinstripe/help/Makefile
creating toolkit/themes/pinstripe/mozapps/Makefile
creating toolkit/themes/winstripe/communicator/Makefile
creating toolkit/themes/winstripe/Makefile
creating toolkit/themes/winstripe/global/Makefile
creating toolkit/themes/winstripe/help/Makefile
creating toolkit/themes/winstripe/mozapps/Makefile
creating toolkit/xre/Makefile
creating calendar/installer/Makefile
creating calendar/installer/windows/Makefile
creating calendar/locales/Makefile
creating calendar/sunbird/Makefile
creating calendar/sunbird/app/Makefile
creating calendar/sunbird/base/Makefile
creating calendar/sunbird/locales/Makefile
creating db/sqlite3/src/Makefile
creating db/morkreader/Makefile
creating storage/Makefile
creating storage/public/Makefile
creating storage/src/Makefile
creating storage/build/Makefile
creating storage/test/Makefile
updating cache ./config.cache
creating ./config.status
creating config/autoconf.mk
creating config/doxygen.cfg
creating gfx/cairo/cairo/src/cairo-features.h
creating xpfe/global/buildconfig.html
creating toolkit/content/buildconfig.html
creating gfx/gfx-config.h
creating netwerk/necko-config.h
creating xpcom/xpcom-config.h
creating xpcom/xpcom-private.h
configuring in nsprpub
running /bin/sh ./configure  --enable-application=calendar --with-dist-prefix=/home/roger/mozilla/dist --with-mozilla --disable-debug --enable-optimize --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for whoami... (cached) /usr/bin/whoami
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... /usr/bin/ar
checking for ld... /usr/bin/ld
checking for strip... /usr/bin/strip
checking for windres... no
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking for perl5... (cached) /usr/bin/perl
checking for dlopen in -ldl... (cached) yes
checking for dlfcn.h... (cached) yes
checking whether gcc needs -traditional... (cached) no
checking for lchown... (cached) yes
checking for strerror... (cached) yes
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
updating cache .././config.cache
creating ./config.status
creating Makefile
creating config/Makefile
creating config/autoconf.mk
creating config/nsprincl.mk
creating config/nsprincl.sh
creating config/nspr-config
creating lib/Makefile
creating lib/ds/Makefile
creating lib/libc/Makefile
creating lib/libc/include/Makefile
creating lib/libc/src/Makefile
creating lib/tests/Makefile
creating pkg/Makefile
creating pkg/linux/Makefile
creating pkg/solaris/Makefile
creating pkg/solaris/SUNWpr/Makefile
creating pkg/solaris/SUNWprd/Makefile
creating pr/Makefile
creating pr/include/Makefile
creating pr/include/md/Makefile
creating pr/include/obsolete/Makefile
creating pr/include/private/Makefile
creating pr/src/Makefile
creating pr/src/io/Makefile
creating pr/src/linking/Makefile
creating pr/src/malloc/Makefile
creating pr/src/md/Makefile
creating pr/src/md/unix/Makefile
creating pr/src/memory/Makefile
creating pr/src/misc/Makefile
creating pr/src/threads/Makefile
creating pr/tests/Makefile
creating pr/tests/dll/Makefile
creating pr/src/pthreads/Makefile
configure: warning: Recreating autoconf.mk with updated nspr-config output
roger@roger-laptop:~/mozilla$ 

```

So, that seemed to run - hoped the last line wasn't important. Then ran make, and a staggering amount of readout finished in...

```
TestMinStringAPI.o: In function `test_adopt_sub()':
TestMinStringAPI.cpp:(.text+0x68a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
TestMinStringAPI.o: In function `test_adopt()':
TestMinStringAPI.cpp:(.text+0x73a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
/usr/bin/ld: TestMinStringAPI: hidden symbol `nsMemory::Clone(void const*, unsigned int)' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[3]: *** [TestMinStringAPI] Error 1
make[3]: Leaving directory `/home/roger/mozilla/xpcom/tests'
make[2]: *** [libs] Error 2
make[2]: Leaving directory `/home/roger/mozilla/xpcom'
make[1]: *** [tier_2] Error 2
make[1]: Leaving directory `/home/roger/mozilla'
make: *** [default] Error 2
roger@roger-laptop:~/mozilla$ 
```


The additional packages I found I needed from the start, by the way, were build-essential libgtk2.0-0 libgtk2.0-dev libidl-dev

You know, until this point I thought I had a chance of getting through this, but there's now so much info I can't digest or even post (due to sheer quantity). Does the above error mean anything to anyone?

Thanks very much to both of you for your help, and I will understand if this is the end of the line!!

Cheers
Roger

Glad to have helped!
Now, the configure script seems to be working, but compilation fails with the error:
```
TestMinStringAPI.o: In function `test_adopt_sub()':
TestMinStringAPI.cpp:(.text+0x68a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
TestMinStringAPI.o: In function `test_adopt()':
TestMinStringAPI.cpp:(.text+0x73a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
```

undefined reference means that there is a call to the function
```
nsMemory::Clone(void const*, unsigned int)
```
which cannot be found in any of the libraries it is linking against, or in headers it is including.
Seems that something is still missing. Let me check and will be right back.

---

### Post by xeth_delta on 2008-09-26
> **rogerdean said:**
> sorry, it's all above now

Is it working now?

---

### Post by xeth_delta on 2008-09-26
Ok, try to install the following:
```
sudo apt-get install libmozjs-dev libmozjs0d
```
Hope it helps.

---

### Post by rogerdean on 2008-09-26
Thanks for sticking with me! You might yet regret it... I'm not sure that helped I'm afraid. Here's the full output attached (the last bit is the same, as far as I can tell)

Cheers
Roger

---

### Post by xeth_delta on 2008-09-27
> **rogerdean said:**
> Thanks for sticking with me! You might yet regret it... I'm not sure that helped I'm afraid. Here's the full output attached (the last bit is the same, as far as I can tell)

Cheers
Roger

Hehe, don't worry, I like to help.
Let me check the output. I might also like tot try to compile it myself to see what happens. Can you give me a link to the page you downloaded the source code from? Is it from sourceforge?

---

### Post by rogerdean on 2008-09-27
great, source is here...

[http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.9/source/lightning-sunbird-0.9-source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.9/source/lightning-sunbird-0.9-source.tar.bz2)

---

### Post by rogerdean on 2008-09-27
...and I've uncovered some mozilla-specific build pages here

[http://www.mozilla.org/projects/calendar/sunbird/build.html](http://www.mozilla.org/projects/calendar/sunbird/build.html)

---

### Post by xeth_delta on 2008-09-27
> **rogerdean said:**
> great, source is here...

[http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.9/source/lightning-sunbird-0.9-source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.9/source/lightning-sunbird-0.9-source.tar.bz2)

Hmmm, I just decomompressed the file. I might be wrong, but that seems like the source code for the browser itself, mozilla. Do you have to compile the whole thing in order to compile songbird, too?

By the way, is there any reason why you might need to compile sunbird from source? There is an installable version from the repositories, already compiled.

---

### Post by xeth_delta on 2008-09-27
> **xeth_delta said:**
> Hmmm, I just decomompressed the file. I might be wrong, but that seems like the source code for the browser itself, mozilla. Do you have to compile the whole thing in order to compile songbird, too?

By the way, is there any reason why you might need to compile sunbird from source? There is an installable version from the repositories, already compiled.

Nevermind, I think I got it. It seems to be the source code for many applications from which you choose with the --enable-aplication flag.

Compiling now, will be back with results.

---

### Post by rogerdean on 2008-09-27
yup, i think that's right, the source is much bigger than sunbird alone would require

all i'm really trying to do is make a .deb for convenience, as it'll be six months or more before 0.9 gets into regular repos...

---

### Post by xeth_delta on 2008-09-27
Had the same problems you did when compiling from the same archive.

I followed the instructions from [http://www.mozilla.org/projects/calendar/sunbird/build.html:](http://www.mozilla.org/projects/calendar/sunbird/build.html:)
```
mkdir sunbird
cd sunbird
cvs -d :pserver:anonymous@cvs-mirror.mozilla.org:/cvsroot co mozilla/client.mk
cd mozilla
make -f client.mk checkout MOZ_CO_PROJECT=calendar
```

That should download the source code for sunbird from CVS.
Apparently, regular configuration and compilation is not recommended. Instead, create a new file and append some lines to it.
```
echo "ac_add_options --enable-application=calendar" >> .mozconfig
echo "mk_add_options MOZ_CO_PROJECT=calendar" >> .mozconfig
echo "ac_add_options --disable-crashreporter" >> .mozconfig
```

and compile:
```
make -f client.mk build
```
Then try to create the deb file as usual. Let us know if it works.

---

### Post by rogerdean on 2008-09-27
great stuff. so what should the new configuration file be called, and where should it be?

i guess after...

```
make -f client.mk build
```

my next command should be...

```
$ sudo checkinstall
```

right?

---

### Post by xeth_delta on 2008-09-27
> **rogerdean said:**
> great stuff. so what should the new configuration file be called, and where should it be?

i guess after...

```
make -f client.mk build
```

my next command should be...

```
$ sudo checkinstall
```

right?

Did it compile? No need to run configure. It will be run automatically by the make line.

Yes, I think the next command should be checkinstall, but I would also add an extra option:
```
checkinstall --install=no
```
So that it is not installed right after creation. You can then move the deb and install with
```
sudo dpkg -i pack_name
```

---

### Post by rogerdean on 2008-09-27
ha! no it takes me a *lot* longer than that to download big stuff. this year i live in herat, on the afghanistan iran border...

might have to leave it to run through the night. will be in touch!

oh yes, and what about that config file? where should i put it and what name?

---

### Post by rogerdean on 2008-09-27
ah, that's ok, your previous code sets the filename and location. still downloading...

---

### Post by rogerdean on 2008-09-27
um... right. well all seems to work now right until...

```
sudo checkinstall --install=no
```

when i get this...

```
roger@roger-laptop:~/sunbird/mozilla$ sudo checkinstall --install=no
[sudo] password for roger: 

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Sunbird 0.9
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@roger-laptop ]
1 -  Summary: [ Sunbird 0.9 ]
2 -  Name:    [ mozilla ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ mozilla ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: Nothing to be done for `install'.

======================== Installation successful ==========================

Copying documentation directory...
./
./docshell/
./docshell/build/
./docshell/build/libdocshell.so
./docshell/build/docshell.pkg
./docshell/build/Makefile
./docshell/build/nsDocShellCID.h
./docshell/build/CVS/
./docshell/build/CVS/Repository
./docshell/build/CVS/Root
./docshell/build/CVS/Entries
./docshell/build/nsDocShellModule.cpp
./docshell/build/.cvsignore
./docshell/build/Makefile.in
./docshell/build/.deps/
./docshell/build/.deps/nsDocShellModule.pp
./docshell/build/nsDocShellModule.o
./docshell/test/
./docshell/test/bug413310-post.sjs
./docshell/test/test_bug94514.html
./docshell/test/bug369814.zip
./docshell/test/bug94514-postpage.html
./docshell/test/Makefile
./docshell/test/navigation/
./docshell/test/navigation/test_not-opener.html
./docshell/test/navigation/test_sibling-matching-parent.html
./docshell/test/navigation/open.html
./docshell/test/navigation/test_bug278916.html
./docshell/test/navigation/test_bug13871.html
./docshell/test/navigation/test_reserved.html
./docshell/test/navigation/navigate.html
./docshell/test/navigation/test_bug386782.html
./docshell/test/navigation/test_bug430723.html
./docshell/test/navigation/parent.html
./docshell/test/navigation/blank.html
./docshell/test/navigation/test_bug430624.html
./docshell/test/navigation/Makefile
./docshell/test/navigation/test_popup-navigates-children.html
./docshell/test/navigation/test_grandchild.html
./docshell/test/navigation/NavigationUtils.js
./docshell/test/navigation/test_opener.html
./docshell/test/navigation/CVS/
./docshell/test/navigation/CVS/Repository
./docshell/test/navigation/CVS/Root
./docshell/test/navigation/CVS/Entries
./docshell/test/navigation/iframe.html
./docshell/test/navigation/test_child.html
./docshell/test/navigation/test_bug279495.html
./docshell/test/navigation/test_sibling-off-domain.html
./docshell/test/navigation/test_bug270414.html
./docshell/test/navigation/Makefile.in
./docshell/test/unit/
./docshell/test/unit/test_nsIDownloadHistory.js
./docshell/test/unit/head_docshell.js
./docshell/test/unit/CVS/
./docshell/test/unit/CVS/Repository
./docshell/test/unit/CVS/Root
./docshell/test/unit/CVS/Entries
./docshell/test/unit/test_bug414201_jfif.js
./docshell/test/test_bug413310.html
./docshell/test/CVS/
./docshell/test/CVS/Repository
./docshell/test/CVS/Root
./docshell/test/CVS/Entries.Log
./docshell/test/CVS/Entries
./docshell/test/test_bug344861.html
./docshell/test/browser/
./docshell/test/browser/browser_bug388121-1.js
./docshell/test/browser/browser_bug349769.js
./docshell/test/browser/Makefile
./docshell/test/browser/browser_bug441169.js
./docshell/test/browser/browser_bug388121-2.js
./docshell/test/browser/CVS/
./docshell/test/browser/CVS/Repository
./docshell/test/browser/CVS/Root
./docshell/test/browser/CVS/Entries
./docshell/test/browser/browser_bug134911.js
./docshell/test/browser/browser_bug92473.js
./docshell/test/browser/test-form_sjis.html
./docshell/test/browser/Makefile.in
./docshell/test/test_bug369814.html
./docshell/test/test_bug384014.html
./docshell/test/test_bug387979.html
./docshell/test/bug404548-subframe.html
./docshell/test/chrome/
./docshell/test/chrome/test_bug396519.xul
./docshell/test/chrome/bug364461_window.xul
./docshell/test/chrome/Makefile
./docshell/test/chrome/test_bug364461.xul
./docshell/test/chrome/CVS/
./docshell/test/chrome/CVS/Repository
./docshell/test/chrome/CVS/Root
./docshell/test/chrome/CVS/Entries
./docshell/test/chrome/test_bug428288.html
./docshell/test/chrome/Makefile.in
./docshell/test/chrome/bug396519_window.xul
./docshell/test/bug413310-subframe.html
./docshell/test/Makefile.in
./docshell/test/test_bug404548.html
./docshell/test/test_bug402210.html
./docshell/Makefile
./docshell/resources/
./docshell/resources/Makefile
./docshell/resources/CVS/
./docshell/resources/CVS/Repository
./docshell/resources/CVS/Root
./docshell/resources/CVS/Entries
./docshell/resources/.cvsignore
./docshell/resources/content/
./docshell/resources/content/Makefile
./docshell/resources/content/CVS/
./docshell/resources/content/CVS/Repository
./docshell/resources/content/CVS/Root
./docshell/resources/content/CVS/Entries
./docshell/resources/content/netError.xhtml
./docshell/resources/content/jar.mn
./docshell/resources/content/.cvsignore
./docshell/resources/content/Makefile.in
./docshell/resources/Makefile.in
./docshell/CVS/
./docshell/CVS/Repository
./docshell/CVS/Root
./docshell/CVS/Entries.Log
./docshell/CVS/Entries
./docshell/shistory/
./docshell/shistory/public/
./docshell/shistory/public/nsISHistoryInternal.idl
./docshell/shistory/public/nsISHEntry.idl
./docshell/shistory/public/Makefile
./docshell/shistory/public/_xpidlgen/
./docshell/shistory/public/_xpidlgen/nsISHContainer.h
./docshell/shistory/public/_xpidlgen/nsISHEntry.h
./docshell/shistory/public/_xpidlgen/nsISHistoryListener.h
./docshell/shistory/public/_xpidlgen/nsISHTransaction.xpt
./docshell/shistory/public/_xpidlgen/nsISHistory.xpt
./docshell/shistory/public/_xpidlgen/.done
./docshell/shistory/public/_xpidlgen/nsISHContainer.xpt
./docshell/shistory/public/_xpidlgen/nsIHistoryEntry.h
./docshell/shistory/public/_xpidlgen/nsISHTransaction.h
./docshell/shistory/public/_xpidlgen/nsISHistoryListener.xpt
./docshell/shistory/public/_xpidlgen/nsISHistoryInternal.h
./docshell/shistory/public/_xpidlgen/nsISHistory.h
./docshell/shistory/public/_xpidlgen/nsISHEntry.xpt
./docshell/shistory/public/_xpidlgen/nsIHistoryEntry.xpt
./docshell/shistory/public/_xpidlgen/shistory.xpt
./docshell/shistory/public/_xpidlgen/nsISHistoryInternal.xpt
./docshell/shistory/public/CVS/
./docshell/shistory/public/CVS/Repository
./docshell/shistory/public/CVS/Root
./docshell/shistory/public/CVS/Entries
./docshell/shistory/public/nsISHContainer.idl
./docshell/shistory/public/nsISHistory.idl
./docshell/shistory/public/.cvsignore
./docshell/shistory/public/nsIHistoryEntry.idl
./docshell/shistory/public/nsISHTransaction.idl
./docshell/shistory/public/nsISHistoryListener.idl
./docshell/shistory/public/Makefile.in
./docshell/shistory/public/.deps/
./docshell/shistory/public/.deps/nsISHistory.pp
./docshell/shistory/public/.deps/nsIHistoryEntry.pp
./docshell/shistory/public/.deps/nsISHistoryListener.pp
./docshell/shistory/public/.deps/nsISHTransaction.pp
./docshell/shistory/public/.deps/nsISHEntry.pp
./docshell/shistory/public/.deps/nsISHContainer.pp
./docshell/shistory/public/.deps/nsISHistoryInternal.pp
./docshell/shistory/Makefile
./docshell/shistory/CVS/
./docshell/shistory/CVS/Repository
./docshell/shistory/CVS/Root
./docshell/shistory/CVS/Entries.Log
./docshell/shistory/CVS/Entries
./docshell/shistory/src/
./docshell/shistory/src/nsSHEntry.h
./docshell/shistory/src/Makefile
./docshell/shistory/src/nsSHistory.h
./docshell/shistory/src/CVS/
./docshell/shistory/src/CVS/Repository
./docshell/shistory/src/CVS/Root
./docshell/shistory/src/CVS/Entries
./docshell/shistory/src/nsSHTransaction.cpp
./docshell/shistory/src/nsSHTransaction.h
./docshell/shistory/src/nsSHTransaction.o
./docshell/shistory/src/libshistory_s.a
./docshell/shistory/src/nsSHEntry.o
./docshell/shistory/src/nsSHistory.o
./docshell/shistory/src/nsSHEntry.cpp
./docshell/shistory/src/.cvsignore
./docshell/shistory/src/nsSHistory.cpp
./docshell/shistory/src/Makefile.in
./docshell/shistory/src/.deps/
./docshell/shistory/src/.deps/nsSHistory.pp
./docshell/shistory/src/.deps/nsSHTransaction.pp
./docshell/shistory/src/.deps/nsSHEntry.pp
./docshell/shistory/.cvsignore
./docshell/shistory/Makefile.in
./docshell/base/
./docshell/base/nsDefaultURIFixup.h
./docshell/base/nsDocShellEditorData.cpp
./docshell/base/nsDocShellLoadInfo.h
./docshell/base/nsAboutRedirector.o
./docshell/base/nsDefaultURIFixup.o
./docshell/base/nsDocShellTransferableHooks.o
./docshell/base/nsDocShell.o
./docshell/base/nsDocShellEditorData.o
./docshell/base/nsDSURIContentListener.o
./docshell/base/nsDownloadHistory.h
./docshell/base/nsIEditorDocShell.idl
./docshell/base/nsDownloadHistory.cpp
./docshell/base/nsGlobalHistoryAdapter.cpp
./docshell/base/nsAboutRedirector.cpp
./docshell/base/nsIDocShellLoadInfo.idl
./docshell/base/nsIWebPageDescriptor.idl
./docshell/base/nsDocShell.h
./docshell/base/crashtests/
./docshell/base/crashtests/crashtests.list
./docshell/base/crashtests/CVS/
./docshell/base/crashtests/CVS/Repository
./docshell/base/crashtests/CVS/Root
./docshell/base/crashtests/CVS/Entries
./docshell/base/crashtests/403574-1.xhtml
./docshell/base/crashtests/369126-1.html
./docshell/base/nsIDownloadHistory.idl
./docshell/base/nsIScrollable.idl
./docshell/base/nsIGlobalHistory2.idl
./docshell/base/nsIURIClassifier.idl
./docshell/base/Makefile
./docshell/base/nsDocShellLoadInfo.o
./docshell/base/nsDocShellEnumerator.h
./docshell/base/_xpidlgen/
./docshell/base/_xpidlgen/nsIDocShellLoadInfo.xpt
./docshell/base/_xpidlgen/nsIGlobalHistory2.xpt
./docshell/base/_xpidlgen/nsIContentViewerFile.xpt
./docshell/base/_xpidlgen/nsIDocShellTreeItem.h
./docshell/base/_xpidlgen/nsIDocShellTreeOwner.xpt
./docshell/base/_xpidlgen/nsIWebNavigation.h
./docshell/base/_xpidlgen/nsIWebPageDescriptor.h
./docshell/base/_xpidlgen/nsIWebPageDescriptor.xpt
./docshell/base/_xpidlgen/nsIWebNavigation.xpt
./docshell/base/_xpidlgen/nsIScrollable.h
./docshell/base/_xpidlgen/nsCDefaultURIFixup.h
./docshell/base/_xpidlgen/nsCDefaultURIFixup.xpt
./docshell/base/_xpidlgen/nsIDocShellHistory.xpt
./docshell/base/_xpidlgen/nsIContentViewer.h
./docshell/base/_xpidlgen/nsIContentViewerEdit.h
./docshell/base/_xpidlgen/nsIDocShell.h
./docshell/base/_xpidlgen/nsITextScroll.xpt
./docshell/base/_xpidlgen/nsIURIClassifier.xpt
./docshell/base/_xpidlgen/nsIDocShellHistory.h
./docshell/base/_xpidlgen/nsIDownloadHistory.h
./docshell/base/_xpidlgen/nsCDocShell.xpt
./docshell/base/_xpidlgen/nsIEditorDocShell.h
./docshell/base/_xpidlgen/nsIDownloadHistory.xpt
./docshell/base/_xpidlgen/nsIURIClassifier.h
./docshell/base/_xpidlgen/nsIDocShellTreeItem.xpt
./docshell/base/_xpidlgen/.done
./docshell/base/_xpidlgen/nsIURIFixup.h
./docshell/base/_xpidlgen/nsIURIFixup.xpt
./docshell/base/_xpidlgen/nsIDocShellTreeNode.h
./docshell/base/_xpidlgen/nsIGlobalHistory2.h
./docshell/base/_xpidlgen/nsIGlobalHistory3.xpt
./docshell/base/_xpidlgen/nsIDocShellTreeOwner.h
./docshell/base/_xpidlgen/nsIScrollable.xpt
./docshell/base/_xpidlgen/nsITextScroll.h
./docshell/base/_xpidlgen/nsIContentViewerEdit.xpt
./docshell/base/_xpidlgen/nsIContentViewer.xpt
./docshell/base/_xpidlgen/nsIContentViewerFile.h
./docshell/base/_xpidlgen/nsIMarkupDocumentViewer.xpt
./docshell/base/_xpidlgen/nsIGlobalHistory3.h
./docshell/base/_xpidlgen/nsIWebNavigationInfo.h
./docshell/base/_xpidlgen/nsIDocShellTreeNode.xpt
./docshell/base/_xpidlgen/nsCDocShell.h
./docshell/base/_xpidlgen/nsIDocShellLoadInfo.h
./docshell/base/_xpidlgen/nsIMarkupDocumentViewer.h
./docshell/base/_xpidlgen/nsIWebNavigationInfo.xpt
./docshell/base/_xpidlgen/nsIGlobalHistory.h
./docshell/base/_xpidlgen/nsIDocShell.xpt
./docshell/base/_xpidlgen/nsIChannelClassifier.h
./docshell/base/_xpidlgen/nsIGlobalHistory.xpt
./docshell/base/_xpidlgen/docshell.xpt
./docshell/base/_xpidlgen/nsIEditorDocShell.xpt
./docshell/base/_xpidlgen/nsIChannelClassifier.xpt
./docshell/base/nsWebNavigationInfo.cpp
./docshell/base/libbasedocshell_s.a
./docshell/base/nsIURIFixup.idl
./docshell/base/nsDSURIContentListener.cpp
./docshell/base/nsIDocShell.idl
./docshell/base/nsITextScroll.idl
./docshell/base/nsIMarkupDocumentViewer.idl
./docshell/base/nsDocShellEditorData.h
./docshell/base/nsDocShellLoadInfo.cpp
./docshell/base/CVS/
./docshell/base/CVS/Repository
./docshell/base/CVS/Root
./docshell/base/CVS/Entries.Log
./docshell/base/CVS/Entries
./docshell/base/nsCDefaultURIFixup.idl
./docshell/base/nsDSURIContentListener.h
./docshell/base/nsIDocShellTreeNode.idl
./docshell/base/nsWebNavigationInfo.o
./docshell/base/nsIContentViewerEdit.idl
./docshell/base/nsWebShell.cpp
./docshell/base/nsDownloadHistory.o
./docshell/base/nsWebNavigationInfo.h
./docshell/base/nsWebShell.o
./docshell/base/nsIDocShellTreeItem.idl
./docshell/base/nsIWebNavigation.idl
./docshell/base/nsCDocShell.idl
./docshell/base/nsIContentViewerFile.idl
./docshell/base/nsIDocShellTreeOwner.idl
./docshell/base/nsIContentViewer.idl
./docshell/base/nsWebShell.h
./docshell/base/nsIChannelClassifier.idl
./docshell/base/nsDocShellLoadTypes.h
./docshell/base/nsIDocShellHistory.idl
./docshell/base/nsIGlobalHistory3.idl
./docshell/base/nsGlobalHistory2Adapter.h
./docshell/base/.cvsignore
./docshell/base/nsGlobalHistoryAdapter.o
./docshell/base/nsDocShellEnumerator.o
./docshell/base/nsDocShellTransferableHooks.cpp
./docshell/base/nsGlobalHistory2Adapter.cpp
./docshell/base/nsDocShell.cpp
./docshell/base/nsIWebNavigationInfo.idl
./docshell/base/nsDocShellEnumerator.cpp
./docshell/base/nsGlobalHistoryAdapter.h
./docshell/base/nsAboutRedirector.h
./docshell/base/nsIGlobalHistory.idl
./docshell/base/Makefile.in
./docshell/base/nsGlobalHistory2Adapter.o
./docshell/base/.deps/
./docshell/base/.deps/nsDocShell.pp
./docshell/base/.deps/nsDocShellTransferableHooks.pp
./docshell/base/.deps/nsIMarkupDocumentViewer.pp
./docshell/base/.deps/nsAboutRedirector.pp
./docshell/base/.deps/nsDocShellEnumerator.pp
./docshell/base/.deps/nsGlobalHistoryAdapter.pp
./docshell/base/.deps/nsDefaultURIFixup.pp
./docshell/base/.deps/nsDocShellEditorData.pp
./docshell/base/.deps/nsIContentViewer.pp
./docshell/base/.deps/nsIDownloadHistory.pp
./docshell/base/.deps/nsDownloadHistory.pp
./docshell/base/.deps/nsIWebNavigation.pp
./docshell/base/.deps/nsIWebNavigationInfo.pp
./docshell/base/.deps/nsGlobalHistory2Adapter.pp
./docshell/base/.deps/nsIScrollable.pp
./docshell/base/.deps/nsIGlobalHistory2.pp
./docshell/base/.deps/nsIEditorDocShell.pp
./docshell/base/.deps/nsIDocShellTreeItem.pp
./docshell/base/.deps/nsIGlobalHistory3.pp
./docshell/base/.deps/nsIDocShellHistory.pp
./docshell/base/.deps/nsDocShellLoadInfo.pp
./docshell/base/.deps/nsIChannelClassifier.pp
./docshell/base/.deps/nsIDocShell.pp
./docshell/base/.deps/nsCDocShell.pp
./docshell/base/.deps/nsIDocShellLoadInfo.pp
./docshell/base/.deps/nsCDefaultURIFixup.pp
./docshell/base/.deps/nsDSURIContentListener.pp
./docshell/base/.deps/nsITextScroll.pp
./docshell/base/.deps/nsIContentViewerEdit.pp
./docshell/base/.deps/nsIWebPageDescriptor.pp
./docshell/base/.deps/nsIURIClassifier.pp
./docshell/base/.deps/nsWebShell.pp
./docshell/base/.deps/nsIDocShellTreeNode.pp
./docshell/base/.deps/nsIGlobalHistory.pp
./docshell/base/.deps/nsWebNavigationInfo.pp
./docshell/base/.deps/nsIContentViewerFile.pp
./docshell/base/.deps/nsIDocShellTreeOwner.pp
./docshell/base/.deps/nsIURIFixup.pp
./docshell/base/nsDefaultURIFixup.cpp
./docshell/base/nsDocShellTransferableHooks.h
./docshell/.cvsignore
./docshell/Makefile.in
./README.txt
./LICENSE
./README/
./README/CVS/
./README/CVS/Repository
./README/CVS/Root
./README/CVS/Entries
./README/mozilla/
./README/mozilla/CVS/
./README/mozilla/CVS/Repository
./README/mozilla/CVS/Root
./README/mozilla/CVS/Entries
./README/mozilla/README.os2
./README/mozilla/README.build
cp: cannot stat `//var/tmp/pZpYBVZefSjfPiAgorDkG/newfiles.tmp': No such file or directory
grep: /var/tmp/pZpYBVZefSjfPiAgorDkG/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: 

```

showing the logfile on offer gives me this...

```
dpkg-deb: parse error, in file `/var/tmp/pZpYBVZefSjfPiAgorDkG/package/DEBIAN/control' near line 10 package `mozilla':
 empty value for version
/var/tmp/pZpYBVZefSjfPiAgorDkG/dpkgbuild.log (END) 

```

none of this happened to you, right? :rolleyes:

---

### Post by rogerdean on 2008-10-02
xeth_delta, thanks so much for your help. I'm going to give up on this now. In any case, merlwiz79 has posted a .deb for Sunbird 0.9

Cheers
Roger

---

