---
title: "Trouble installing Mousetrap"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-04-13
I'm trying to install Mousetrap from the website. I did everything the website told me to do. I got an error saying:
```
configure: error: Could not find python headers needed to build Python extensions
```
The website said If I got this error, I need to install python2.6-dev. I did so and tried to build Mousetrap again. I got the same error again. Just to be sure, I tried to install python2.6-dev again. Same error. HELP!!!!!
```
thomas@Thomas-HP-Mini-5101:~$ git clone git://git.gnome.org/mousetrap
Cloning into 'mousetrap'...
remote: Counting objects: 1354, done.
remote: Compressing objects: 100% (1111/1111), done.
remote: Total 1354 (delta 781), reused 440 (delta 204)
Receiving objects: 100% (1354/1354), 1.74 MiB | 352 KiB/s, done.
Resolving deltas: 100% (781/781), done.
thomas@Thomas-HP-Mini-5101:~$ cd mousetrap
thomas@Thomas-HP-Mini-5101:~/mousetrap$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.68
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.3
checking for libtool >= 1.5...
  testing libtoolize... found 2.4.2
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.32.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.50.2
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 3.1.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-common...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
configure.in:43: installing `./config.guess'
configure.in:43: installing `./config.sub'
configure.in:6: installing `./install-sh'
configure.in:6: installing `./missing'
src/mousetrap/Makefile.am:3: installing `./py-compile'
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for XML::Parser... ok
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for library containing strerror... none required
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for a Python interpreter with version >= 2.6... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for headers required to compile python extensions... not found
configure: error: Could not find python headers needed to build Python extensions
thomas@Thomas-HP-Mini-5101:~/mousetrap$ sudo apt-get install python2.6-dev
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 153 not upgraded.
thomas@Thomas-HP-Mini-5101:~/mousetrap$ 

```

---

### Post by 2F4U on 2012-04-13
Maybe a problem with the path variable, since by default, Ubuntu uses Python 2.7.

---

### Post by doppel.ganger on 2012-04-13
Sorry. That kind of stuff goes way over my head.

---

