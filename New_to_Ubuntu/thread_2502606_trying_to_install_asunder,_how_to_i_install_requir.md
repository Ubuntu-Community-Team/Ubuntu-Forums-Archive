---
title: "trying to install asunder, how to i install required package?"
date: 2024-11-21
forum: New to Ubuntu
---

### Post by mattmcd911 on 2024-11-21
Hello,

I'm trying to install the CD ripping software Asunder on my Linux  advice, but it doesn't appear to be working. This is the output after I  try to ./configure the unzipped file in my downloads:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a race-free mkdir -p... /usr/bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for intltool >= 0.34.90... 0.51.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.38.2
checking for XML::Parser... ok
checking whether make supports the include directive... yes (GNU style)
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to enable C11 features... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether the compiler supports GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to enable C11 features... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether the compiler supports GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to enable C11 features... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for stdio.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for strings.h... yes
checking for sys/stat.h... yes
checking for sys/types.h... yes
checking for unistd.h... yes
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gtk+-2.0 >= 2.4.0, gthread-2.0 >= 2.4.0, libcddb >= 0.9.5... no
configure: error: Package requirements (gtk+-2.0 >= 2.4.0, gthread-2.0 >= 2.4.0, libcddb >= 0.9.5) were not met:

Package 'libcddb', required by 'virtual:world', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Where do I go from here? Please let me know if you need additional information or more context. Thank you.

---

### Post by Dennis N on 2024-11-21
asunder is in the Ubuntu repository. Install it from there for best results.
In terminal:

sudo apt install asunder

---

### Post by mattmcd911 on 2024-11-21
omg i'm such an idiot lol, i was losing my mind for like an hour trying to install it. thank you so much for your help!

---

