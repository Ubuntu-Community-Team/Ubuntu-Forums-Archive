---
title: "Building an arbitrary Gnome project (gnome-media)"
date: 2011-11-07
forum: Programming Talk
---

### Post by jeff.biggeek02 on 2011-11-07
Hello,

I'm trying to learn how to build Gnome, so that I can contribuute to the various projects.  Since you have to start somewhere, I'm trying to build gnome-media. :)

[http://git.gnome.org/browse/gnome-media/](http://git.gnome.org/browse/gnome-media/)

I pulled the code with git, installed the documentation tools per [http://developer.gnome.org/gnome-devel-demos/unstable/getting-ready](http://developer.gnome.org/gnome-devel-demos/unstable/getting-ready).

I'm not sure what steps properly build my output.  Tyipcally, I know Linux has a "./configure" and "make all" 2-step approach.  So I tried ./configure, and I get this output (with an error about AS_COMPILER_FLAG).  Can anyone give me some guidance on building this?

(output from ./configure)

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
./configure: line 3118: AS_VERSION: command not found
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool >= 0.35.0... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.12.4
checking for XML::Parser... ok
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for library containing strerror... none required
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
./configure: line 6387: syntax error near unexpected token `-Wall,'
./configure: line 6387: `AS_COMPILER_FLAG(-Wall, GM_ERROR_CFLAGS="-Wall")'

---

### Post by Bachstelze on 2011-11-07
Gnome is perhaps the most complicated piece of software to compile in the whole world so since you don't seem too familiar with compiling, I suggest you start with something easier.

---

