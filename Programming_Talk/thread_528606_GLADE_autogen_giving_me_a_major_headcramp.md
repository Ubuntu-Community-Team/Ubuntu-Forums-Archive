---
title: "GLADE autogen giving me a major headcramp"
date: 2007-08-18
forum: Programming Talk
---

### Post by kmartens on 2007-08-18
Hi all.
I am really hoping that someone can help me out here....
I have a new installation of Ubuntu - installed GLADE & all the dev tools (I think...) but when I try ./autogen.sh, I get the following spew, which is notably confusing to me...Cannot figure out what the problem is...

klay@klay-linux:~/cims$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 4825: syntax error near unexpected token `PACKAGE,'
./configure: line 4825: `PKG_CHECK_MODULES(PACKAGE, $pkg_modules)'

and here is config.log...

Any suggestions or ideas out there????

---

### Post by fct on 2007-08-18
Don't use glade code generation, it's deprecated. Use libglade instead to load the .glade files and connect the signal handlers on the fly. That way you can change the interface without recompiling the program, and do some other nifty tricks.

And install glade-3, it's the latest version.

---

