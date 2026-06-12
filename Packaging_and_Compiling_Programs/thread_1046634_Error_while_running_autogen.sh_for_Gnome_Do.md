---
title: "Error while running autogen.sh for Gnome Do"
date: 2009-01-21
forum: Packaging and Compiling Programs
---

### Post by teranex on 2009-01-21
Hi,

I would like to have a look at the sourcecode at the sourcecode of Gnome Do (and eventually try to fix some bugs). I checked it out with 'bzr branch lp:do', and was told to run the autogen.sh script afterwards. When i did this the first time i was missing libtool. So i installed it with 'sudo apt-get install libtool'. Then i got an error which i found could be solved by installing libgconf2-dev, which i also did with 'sudo apt-get install libgconf2-dev'. But now i'm getting the following error when running autogen.sh: 'configure: error: cannot run /bin/bash ./config.sub'. Could somebody point me in the right direction on how to fix this? I searched google about this but most of the solutions told me to install libtool, which i already did...

Here is the complete output of the autogen.sh script:
```

jeroen@thunderbox /media/cryptdata/dev/repos/do
$ ./autogen.sh 
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running libtoolize ...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running aclocal -I . -I m4/shamrock  ...
Running automake --gnu  ...
configure.ac: installing `./install-sh'
configure.ac: installing `./mkinstalldirs'
configure.ac: installing `./missing'
configure.ac:5: option `tar-pax' not recognized
Running autoconf ...
Running intltoolize --force --copy --automake ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
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
checking dependency style of gcc... none
checking for intltool >= 0.35.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  ar ast bg br ca cs da de el en_AU en_CA en_GB es et fa fi fr ga hu id is it ja lt lv mk nb nl nn pl pt_BR pt ru sk sl sr sv ta te th tr uk vi zh_CN zh_HK zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for ANSI C header files... (cached) yes
checking for gmcs... /usr/bin/gmcs
checking for LINQ flag for mcs... none needed
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: error: cannot run /bin/bash ./config.sub

```

---

